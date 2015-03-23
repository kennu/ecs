# ECS Wrapper (Amazon EC2 Container Service control tool)
Kenneth Falck <kennu@iki.fi> 2015

This is a simple wrapper around the AWS CLI (http://aws.amazon.com/cli/) to
let you manage ECS slightly more easily. You must already have the AWS CLI
installed and configured, so that the 'aws' command is able to access your
AWS cloud environment.

You also need to have an existing 'default' cluster on ECS. This wrapper
currently always uses the default cluster.

## Examples

Register a Task Definition, using the basename (myapp) as the task family:

    ./ecs regdef myapp.json

Show the current state of defined and running tasks:

    ./ecs ps

Run a task, giving the family as the argument:

    ./ecs run myapp

Stop a task, giving the family as the argument:

    ./ecs stop myapp

## Caveats

The ECS Wrapper always uses the latest Task Definition revision available.
If you register a new task definition revision, you need to stop any running
task of that family and start a new one, to make it appear in 'ecs ps'.

The current version has been used only for controlling a single EC2 instance
(no clustering features).
