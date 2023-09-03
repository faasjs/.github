## Hi there 👋

FaasJS is an Atomic Application Framework based on Typescript.

## Features

**High development efficiency**

The atomized development model can reduce development and iteration to a featherweight level and is more friendly to team development.

FaasJS officially provides plugins such as HTTP, Knex, etc., so that developers can start developing business immediately.

**High maintainability**

The FaaS architecture guarantees the independence between cloud functions and prevents a single error from causing the failure of the entire system.

FaasJS has built-in automated testing tools to facilitate developers to automate the testing of cloud functions.

**High scalability**

FaasJS has a simple and easy-to-use plug-in mechanism that allows developers to extend functions and plugins freely.

## Quickstart

```bash
npx create-faas-app --name faasjs --example --noprovider
```

## Playground

[Fork and open in codespace or your computer.](https://github.com/faasjs/starter)

### Cloud function's file

```ts
// index.func.ts
// all cloud function file should be ended with .func.ts
import { useFunc } from '@faasjs/func'
import { useHttp } from '@faasjs/http'

export default useFunc(function() {
  useHttp() // use http plugin

  return async function () {
    return 'Hello, world' // response content
  }
})
```

## Unit test's file

```ts
// __tests__/index.test.ts
// all unit test file should be ended with .test.ts
import { test } from '@faasjs/test'
import Func from '../index.func'

describe('index', function () {
  it('should work', async function () {
    // wrap the cloud function
    const func = test(Func);

    // mock the request
    const { statusCode, data } = await func.JSONhandler()

    // expect the response with 200 status
    expect(statusCode).toEqual(200)
    // expect the response content is 'Hello, world'
    expect(data).toEqual('Hello, world')
  });
});
```

[Official website](https://faasjs.com)

[CHANGELOG](https://github.com/faasjs/faasjs/blob/main/CHANGELOG.md)

[CONTRIBUTING](https://github.com/faasjs/faasjs/blob/main/CONTRIBUTING.md)

[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Ffaasjs%2Ffaasjs.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Ffaasjs%2Ffaasjs)
