# Workfile v1.1.0 Specifications (DRAFT Release)
* Expecting PRs
* First draft - 13th September, 2022*

## Syntax
- A workfile is written in a simple text format very much inspired by the markdown format.
- A workfile has its extension .work
- Each line in a workfile has a distinct purpose. It has to be one of the variables that defines a project
- The spec follows the syntax as __TOKEN_CHARACTER__ <space> *Corresponding information* eg. `# Namespace / Project Name`, `@username`, etc
- Multiline description is supported. Each line starting without any special token represents the description and description is supported by projects, tasks and milestones
 - Indententation is ignored. However recommeded for legibility 
  
## Terminology
- **Namespace** : Department or something similar
- **Project** : The project (the macro definition of what needs to be done) in few words
- **deadline** : The last day to finish something
- **Milestone** : Usually a checklist with deadline
- **Task** : A smallest unit of job to be finished 
- **Users** : Direct members involved in a project, milestone or task eg. @johndoe
- **Groups** : The set of predefined members involved in a project eg. managers
- **Priority** : A descriptive word to define the intensity of a job eg. high, low, etc

## Tokens
Tokens define the grammar of a workfile.
| Workfile Token 	| Corresponding project parameter 	| Query Params 	|
|----------------	|-----------------------------------------------	|----------------------------------------------------------------------------	|
| # 	| Namespace or Project Name 	| # Sysadmin / Hardware Upgrade and Migration 	|
| @ 	| User, whom the task / project is assigned to 	| @johndoe 	|
| @@ 	| Group, whom the task / project is assigned to 	| @@sysadmin 	|
| > 	| Starting date or Deadline 	| > 2020-04-11 > 2020-04-30 	|
| `no token` | A line in any paragraph (desc) 	| (No token means a description text). ... 	|
| ## 	| Milestone 	| ## Hardware Procurement 	|
| $ 	| Priority 	| $ High 	|
| - 	| A task 	| - Vendor Finalizing 	|
| -- 	| A subtask 	| -- Vendor Assessment |
| -- -- | Another subtask under a subtask | -- -- Any level of subtask can be created |
| ** | A line of comment | ** This is a comment | 


## Sample workfile
Some of the sample workfiles are available in this repo. A simple workfile looks like :
```
** A sample workfile
** This is a comment
** Comment is ignored by parsers
** Comments start with a `*` character

# Namespace/ProjectName
@someuser
@@somegroup
> startdate > deadline

## A milestone
$ Priority
Project description text ...
Project description text second line
project description text third line

** Tasks
- Task 1
  -- subtask 1.1
  -- subtask 1.2
  -- -- sub-subtask 1.2.1
  -- -- sub-subtask 1.2.2
- Task 2
- Task 3

## Another milestone
> milestone-deadline

** Desc
milestone description text (singleline)

** Tasks
- Task 5
- Task 6
  -- subtask 6.2
```

## Limitations
- Subtask don't support assignment, deadlines or any properties. Subtasks are simple checklists
- Attachments currently unsupported, however one can use markdown embed any links as required

## Compatibility with Markdown
- Bolds, Italics are supported as is
- Hyperlinks should work as is
- Markdown and Workfile parsers need to be separately run. Desc blocks can me checked with markdown for more features and rich text supports

