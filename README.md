# Self-service and controlled release to your kubernetes clusters running anywhere

Use Github, Azure Arc for Kubernetes and Azure policy to control application release at scale. Your product teams can have control over when and where to release their applications. Yet the release process is standardized and managed.

## Overview

The diagram below describes in more details the worflow:

![workflow](https://backofficestore.blob.core.windows.net/blogs/images/github-arc.png)

1. The platform or Kubernetes operator maintains central configuration that applies to all Kubernetes clusters managed by Azure Arc for Kubernetes. When a new application is introduced, she defines which clusters in what locations will get this application deployed. This might include defining staging and production versions in separate Kuberenetes namespaces
2. The product team working on an application follow Continuous Integration practices where they continuously push into a central branch in their Github repo. This triggers a Githib workflow which builds, tests and on success creates a docker image of the application
3. At any time, a product team member whether a Product Manager, engineer or else can decide to promote a specific app version. By submitting a Pull Request to change a specific release file, the change will be automatically checked through an automated process. With code review and inspection the request can possibly get approved. If a deployment is required on a staging version in one cluster in Europe for example, the release file under Staging/Europe folder wil need to be modified.
4. Using Azure Arc Agent the various kubernetes clusters are continuously polling for changes in release files that they have been configured against

## Benefits
+ Developers use a simple self-service approach to release or rollback their applications to multiple locations
+ Company wide standards and policies apply on all applications running anywhere
+ Product teams can select whatever tooling they require to build and push docker images. Yet application push is always standardized

## Try it 

Follow the steps below to try the workflow yourself

>Steps go here

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
