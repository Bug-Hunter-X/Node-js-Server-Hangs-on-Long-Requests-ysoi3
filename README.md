# Node.js Server Hang on Long Requests
This repository demonstrates a common issue in Node.js servers where long-running requests can cause the server to hang and become unresponsive.  The example shows a server that simulates a long-running task without proper asynchronous handling.  This can lead to a denial-of-service condition if many such requests are made.

## Problem
The provided `server.js` uses a `while` loop to simulate a 5-second delay.  In a real-world scenario, this could be a database query, file processing, or other I/O-bound operation.  Because Node.js is single-threaded, this blocks the event loop preventing any other requests from being handled.

## Solution
The `serverSolution.js` provides a solution using asynchronous techniques (Promises or async/await) to prevent blocking of the event loop.  This allows other requests to be processed concurrently, keeping the server responsive.

## How to run
1.  Clone the repository: `git clone https://github.com/yourusername/node-server-hang.git`
2.  Navigate to the repository: `cd node-server-hang`
3.  Install dependencies (none are required for this example)
4.  Run the buggy server: `node server.js`
5.  Run the corrected server: `node serverSolution.js`

Test the servers by making multiple requests using tools like `curl` or a browser.