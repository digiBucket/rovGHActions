------
Create a Container Action Using GitHub Actions
- To optimize the performance of our app, we need to check the memory allocated to the container during build time. 
Using GH Action, we send input and output params to the runner to insert a greeting & get total memory from the build logs.

1. Create a Shell Script to Output Memory Info ("entrypoint.sh")

#!/bin/sh

echo "Hello $INPUT_MYINPUT"                             //builtin var
memory=$(cat /proc/meminfo)                                //another env variable   (meminfor for linux is located here)
echo "::set-output name=memory::$memory"         //github syntax to output var into the action is ::

2. Create a Container to Run the Action ("Dockerfile")

FROM debian:9.5-slim
ADD entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

3. Add  "action.yml"

name: 'my first container action'
description: 'A cloud guru'
author: 'Rov Sattha'
inputs:
  myInput:
    description: 'greeting to use'
    required: true
    default: 'Awesome Guru'
outputs:
  myOutput:
    description: 'total memory'
runs:
  using: 'docker'
  image: 'Dockerfile'


4. Add Workflow ".github/workflows/workflow.yml" 

on: [push]

jobs:
  my-job:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: run the action
      id: hello
      uses: ./
      with:
        myInput: 'Chad'
    - name: output the memory
      run: |
        echo ${{ steps.hello.outputs.memory }}
        echo "total memory successfully output"



Expand the run the action step and verify the hello greeting.
Expand the output and verify the presence of the "total memory successfully output" message.