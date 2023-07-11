# API Gateway between ChatGPT custom plugin and backend APIs

API Gateway can be helpful for ChatGPT plugin developers to expose, secure, manage, and monitor their API endpoints. 
This repo demonstrates how to use [Apache APISIX](https://apisix.apache.org/) API Gateway as a front door for communication between ChatGPT custom plugins
and backend APIs.

## How does it work?

As an example, in the [ChatGPT user interface](https://chat.openai.com/), if a user wants to obtain details about a speaker's sessions and topics using either the speaker's unique ID or name,
the plugin is capable of establishing a connection with the plugin service. It then forwards the user's request to the API Gateway, which retrieves the necessary information 
from various API endpoints and consolidates the response into a unified context. See sample output below:

![API Gateway for ChatGPT Plugins](https://github.com/Boburmirzo/apisix-chatgpt-gateway-plugin/assets/14247607/746ea134-f656-4ea8-bbd8-16cfca6f6837)

Assume that now you want to secure the Conference API, **without API Gateway** in place you can still secure the data exchange between ChatGPT UI and plugin by using [Plugin Authentication](https://platform.openai.com/docs/plugins/authentication) methods from OpenAI. However, the communication between the plugin and your backend service **still remains unsecured** until you implement some cross-cutting concerns in Python code, instead of spending time on this:
    - We can implement security measures like **authentication, authorization, and rate limiting** with the API Gateway to protect the Conference API from unauthorized access and potential attacks. ChatGPT can talk to API Gateway freely but the communication between API Gateway and backend service can be absolutely secure.

## How to run it?

### Prerequisites

- Before you start, it is good to have a basic understanding of APISIX. Familiarity with API gateway, and its key concepts such as [routes](https://docs.api7.ai/apisix/key-concepts/routes), [upstream](https://docs.api7.ai/apisix/key-concepts/upstreams), [Admin API](https://apisix.apache.org/docs/apisix/admin-api/), [plugins](https://docs.api7.ai/apisix/key-concepts/plugins), and HTTP protocol will also be beneficial.
- [Docker](https://docs.docker.com/get-docker/) is used to install the containerized etcd and APISIX.
- Download [Visual Studio Code](https://code.visualstudio.com/) compatible with your operating system, or use any other code editor like [IntelliJ IDEA](https://www.jetbrains.com/idea/), [PyCharm](https://www.jetbrains.com/pycharm/), etc.
- To develop custom **ChatGPT Plugins** you need to have a [ChatGPT Plus](https://openai.com/blog/chatgpt-plus) account and [join the plugins waitlist](https://openai.com/waitlist/plugins).

To start the project run simply the following command from the project root directory:

```yaml
docker compose up
```

### Community

🙋 [Join the Apache APISIX Community](https://apisix.apache.org/docs/general/join/)

🐦 [Follow us on Twitter](https://twitter.com/ApacheAPISIX)

📝 [Find us on Slack](https://join.slack.com/t/the-asf/shared_invite/zt-vlfbf7ch-HkbNHiU_uDlcH_RvaHv9gQ)

💁 [How to contribute page](https://apisix.apache.org/docs/general/how-to-contribute/)

### About the author

Follow me on Twitter: [@BoburUmurzokov](https://twitter.com/BoburUmurzokov)

Visit my blog: [www.iambobur.com](https://www.iambobur.com/)
