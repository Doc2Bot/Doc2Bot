# Doc2Bot
Source code and full dataset will be committed after legal review.

## Dataset Description

`samples/` include the examples from 4 domains (`Public Service` domain is not available for legal considerations). For
each domain, there are one `documents/` and `dialogs/`.

### Documents

For each document, there is a JSON file named `name.json`. Each document instance includes the following:

- `document_id`: the ID of a document;
- `domain`: the domain of a document;
- `name`: the name of the document;
- `graph`: key-value pairs of all nodes in the document graph, with `node_id` as the key. Each node includes the
  following:
    - `data`: the data of a node;
    - `type`: the type of node, including the following:
        - **disjunction** indicates that all the following conditions should be satisfied.
        - **conjunction** indicates that at least one of the following conditions should be satisfied.
        - **condition** indicates the node describes a condition.
        - **solution** indicates the node describes a solution.
        - **negation** indicates the following condition can't be satisfied.
        - **table** indicates the following nodes are in a table structure.
        - **object** indicates the node is an object in a table.
        - **attribute** indicates the node is an attribute of an object.
        - **value** indicates the node is a value of an attribute.
        - **sequence** indicates the node is a sequence of steps.
        - **sequence-step** indicates the node is one step in a sequence of steps.
        - **see-more** indicates the node will link to another node that has additional information.
        - **ordinary** indicates the node belongs to none of the above.
    - `pid`: the parent node id;

### Dialogs

For each dialog, there is a JSON file named  `dialog_id.json`. Each dialog instance has several turns that include the
following:

- `turn`: the ID of a turn;
- `role`: the role of a turn;
- `utterance`: the utterance of a turn;
- `act`: the dialog act of a turn, different role has different dialog act:
    - For User:
        - **what** means the user asks a **what** question.
        - **when** means the user asks a question for a time or date.
        - **where** means the user asks a question for a location.
        - **why** means the user asks a question for a reason.
        - **how** means the user wants to know the way to do something.
        - **verification** means the user asking a question to verify something.
        - **ans/open** means the user gives an open answer to the system's question.
        - **ans/yesno** means the user confirms and denies partly the system's question.
        - **ans/yes** means the user confirms the system's question.
        - **ans/no** means the user denies the system's question.
    - For System:
        - **question/open** means the system asks an open question.
        - **multiple-choice** means the system asks a multiple-choice question.
        - **verification** means the system asks a question to verify something.
        - **ans/open** means the system gives an open answer to the user's question.
        - **ans/yesno** means the system confirms and denies partly the user's question.
        - **ans/yes** means the system confirms the user's question.
        - **ans/no** means the system denies the user's question.
- `document`: the document file name of the grounding nodes
- `grounding`: grounding node text
- `grounding_id`: grounding node id
