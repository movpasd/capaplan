# Functional specification

## Requirements

`capaplan` is a command-line tool for capacity planning. It is meant to help plan out and then track
hours or days worked on different projects. This section details lists the feature requirements for
v1 of `capaplan`.

- [ ] Creating and managing multiple ledgers in different folders
- [ ] Stateful CLI
- [ ] Multiple projects within a ledger
- [ ] Creating plans: Projected amounts of time spent on each project within a period
- [ ] Logging time (like filling out a timesheet)
- [ ] Option for interactive or non-interactive CLI
- [ ] Multiple users
- [ ] State is immutable by default: Full history of every change recorded (or should it be? e.g.:
  should a project description be properly editable? Certainly all business logic must be immutable,
  but not sure if metadata should be mutable)
- [ ] CLI reports


## Model

The *ledger* is the top-level object containing the state of a `capaplan` instance. (I would use the
word "project", but this is confusing because capacity planning is supposed to track time across
many "projects". I also thought of using "planner", but this would be confusing next to individual
"plans", individual projections/milestones.) Each ledger can have a name and a description. Each
ledger corresponds to a single file stored in the file system.

Each ledger can have a number of *projects* attached. Projects are like buckets which can store
time planned or tracked against them. Projects can have a slug, a name, and and a description.
They can be archived, but they cannot be directly deleted (see `muta` for details).

Every ledger has a *default project*, which has the name `"(default)"`, slug `"default"`. It can't
be archived.




## CLI

* `capa`
  * `init` -- create new ledgers
  * `proj` -- manage projects
    * `list`
    * `info`
    * `new`
    * `edit`
    * `del` or `rm`
  * `plan`
    * `list`
    * `info`
    * `new`
    * `edit`
    * `del` or `rm`
  * `fill`
  * `muta` -- change history
  * `conf` -- tool configuration
