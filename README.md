# Machine readable testcases for RFC8040 (restconf).

The content of this repository was mostly copied from
IETF RFC 8040 (Restconf) and transformed into machine readable
form by Henning Rogge <henning.rogge@fkie.fraunhofer.de>.

See https://tools.ietf.org/html/rfc8040 for details.

## repository structure

* tests *all defined testcases, each in a subdirectory*
* yang-models *yang models used in the testcases*
* LICENCE *licence as specified by RFC 8040*
* README.md *this file*

## testcase description

Each testcase has a **test.json** file which describes the test and its
parameters, which has the following structure:

```
{
    "name": "<name of the testcase>",
    "yangdirs": [ <list of paths to look for yang files> ],
    "model": "<path of YANG library file to load>",
    "before": "<path of JSON file that describes the datastore
               content before the test",
    "query": {
        "operation": "<http method in upper case>",
        "url": "<URL for the test below the /restconf path>",
        "headers": {
            <A list of HTTP header key/value strings that should
            be set for the query>
        },
        "body": <path of a XML or JSON file to be send in text
                as the query body or NULL if no body should be sent>
    },
    "rpc": {
        "datapath": "<yang schema datapath the RPC should handle>",
        "input": <file with expected input of RPC or NULL for no input",
        "output": <file with expected output of RPC or NULL for no output"
    }
    "response": {
        "status": <expected numeric status code>,
        "headers": {
            <A list of HTTP header key/value strings that must
            be present in the response>
        },
        "body": <path of a XML or JSON file that should be in the
                body of the response or NULL for no response body>
    },
    "after": "<path of JSON file that describes the datastore
               content afterthe test"
}
```
You will find a JSON schema file in the test directory.
