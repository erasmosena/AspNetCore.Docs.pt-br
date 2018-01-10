---
title: Ferramentas do Visual Studio para Docker com ASP.NET Core
description: "Este artigo explica como usar as ferramentas do Visual Studio 2017 e o Docker para Windows para colocar um aplicativo ASP.NET Core em contêineres."
keywords: "Docker,ASP.NET Core,Visual Studio,contêiner"
author: spboyer
ms.author: scaddie
manager: wpickett
ms.date: 09/26/2017
ms.topic: article
ms.prod: asp.net-core
ms.technology: aspnet
ms.assetid: 1f3b9a68-4dea-4b60-8cb3-f46164eedbbf
uid: publishing/vs-tools-for-docker
ms.openlocfilehash: 2d8e337141ae4e0d0258f1d7546510b0ab077e39
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2017
---
# <a name="visual-studio-tools-for-docker"></a><span data-ttu-id="3f5e7-104">Ferramentas do Visual Studio para Docker</span><span class="sxs-lookup"><span data-stu-id="3f5e7-104">Visual Studio Tools for Docker</span></span>

<span data-ttu-id="3f5e7-105">O [Microsoft Visual Studio 2017](https://www.visualstudio.com/) com [Docker para Windows](https://docs.docker.com/docker-for-windows/install/) dá suporte ao build, depuração e execução de aplicativos Web e de console do .NET Framework e .NET Core usando contêineres do Windows e do Linux.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-105">[Microsoft Visual Studio 2017](https://www.visualstudio.com/) with [Docker for Windows](https://docs.docker.com/docker-for-windows/install/) supports building, debugging, and running .NET Framework and .NET Core web and console applications using Windows and Linux containers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f5e7-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3f5e7-106">Prerequisites</span></span>

- <span data-ttu-id="3f5e7-107">[Microsoft Visual Studio 2017](https://www.visualstudio.com/) com carga de trabalho do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f5e7-107">[Microsoft Visual Studio 2017](https://www.visualstudio.com/) with .NET Core workload</span></span>
- [<span data-ttu-id="3f5e7-108">Docker para Windows</span><span class="sxs-lookup"><span data-stu-id="3f5e7-108">Docker for Windows</span></span>](https://docs.docker.com/docker-for-windows/install/)

## <a name="installation-and-setup"></a><span data-ttu-id="3f5e7-109">Instalação e configuração</span><span class="sxs-lookup"><span data-stu-id="3f5e7-109">Installation and setup</span></span>

<span data-ttu-id="3f5e7-110">Instale o [Microsoft Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio) com a carga de trabalho do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-110">Install [Microsoft Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio) with the .NET Core workload.</span></span> <span data-ttu-id="3f5e7-111">Caso você já tenha o Visual Studio instalado, é possível [modificar a sua instalação do Visual Studio](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) para adicionar a carga de trabalho do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-111">If you already have Visual Studio installed, you can [modify your Visual Studio installation](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) to add the .NET Core workload.</span></span>

<span data-ttu-id="3f5e7-112">Para a instalação do Docker, examine as informações em [Docker for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker para Windows: o que saber antes de instalar) e instale o [Docker para Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="3f5e7-112">For Docker installation, review the information at [Docker for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) and install [Docker For Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

<span data-ttu-id="3f5e7-113">É uma configuração necessária para instalação de **[Unidades Compartilhadas](https://docs.docker.com/docker-for-windows/#shared-drives)** no Docker para Windows.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-113">A required configuration is to setup **[Shared Drives](https://docs.docker.com/docker-for-windows/#shared-drives)** in Docker for Windows.</span></span> <span data-ttu-id="3f5e7-114">A configuração é necessária para o mapeamento do volume e suporte à depuração.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-114">The setting is required for the volume mapping and debugging support.</span></span>

<span data-ttu-id="3f5e7-115">Clique com o botão direito do mouse no ícone do Docker na Bandeja do Sistema, clique em **Configurações** e selecione **Unidades Compartilhadas**.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-115">Right-click the Docker icon in the System Tray, click **Settings**, and select **Shared Drives**.</span></span> <span data-ttu-id="3f5e7-116">Selecione a unidade em que o Docker armazenará seus arquivos e faça as alterações.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-116">Select the drive where Docker will store your files and apply changes.</span></span>

![Unidades Compartilhadas](./visual-studio-tools-for-docker/_static/settings-shared-drives-win.png)

## <a name="create-an-aspnet-web-application-and-add-docker-support"></a><span data-ttu-id="3f5e7-118">Criar um Aplicativo Web ASP.NET e adicionar suporte ao Docker</span><span class="sxs-lookup"><span data-stu-id="3f5e7-118">Create an ASP.NET Web Application and add Docker Support</span></span>

<span data-ttu-id="3f5e7-119">Usando o Visual Studio, crie um novo Aplicativo Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-119">Using Visual Studio, create a new ASP.NET Core Web Application.</span></span> <span data-ttu-id="3f5e7-120">Quando o aplicativo é carregado, selecione **Adicionar Suporte ao Docker** no **Menu Projeto** ou clique com o botão direito do mouse no projeto no Gerenciador de Soluções e selecione **Adicionar** > **Suporte ao Docker**.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-120">When the application is loaded, either select **Add Docker Support** from the **Project Menu** or right-click the project from the Solution Explorer and select **Add** > **Docker Support**.</span></span>

<span data-ttu-id="3f5e7-121">*Menu Projeto*</span><span class="sxs-lookup"><span data-stu-id="3f5e7-121">*Project Menu*</span></span>

![Projeto Adicionar Suporte ao Docker](./visual-studio-tools-for-docker/_static/project-add-docker-support.png)

<span data-ttu-id="3f5e7-123">*Menu de Contexto do Projeto*</span><span class="sxs-lookup"><span data-stu-id="3f5e7-123">*Project Context Menu*</span></span>

![Clique com o botão direito do mouse em Adicionar Suporte ao Docker](./visual-studio-tools-for-docker/_static/right-click-add-docker-support.png)

<span data-ttu-id="3f5e7-125">Quando você adiciona suporte do Docker ao seu projeto, é possível escolher entre contêineres do Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-125">When you add Docker support to your project, you can choose either Windows or Linux containers.</span></span> <span data-ttu-id="3f5e7-126">(O host do Docker deve estar executando o mesmo tipo de contêiner.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-126">(The Docker host must be running the same container type.</span></span> <span data-ttu-id="3f5e7-127">Se for necessário, altere o tipo de contêiner na instância do Docker em execução, clique com o botão direito do mouse no ícone do **Docker** na Bandeja do Sistema e escolha **Alterar para contêineres do Windows** ou **Alterar para contêineres do Linux**.)</span><span class="sxs-lookup"><span data-stu-id="3f5e7-127">If you need change the container type in the running Docker instance, right-click the **Docker** icon in the System Tray, and choose **Switch to Windows containers** or **Switch to Linux containers**.)</span></span> 

<span data-ttu-id="3f5e7-128">Os seguintes arquivos são adicionados ao projeto:</span><span class="sxs-lookup"><span data-stu-id="3f5e7-128">The following files are added to the project:</span></span>

- <span data-ttu-id="3f5e7-129">**Dockerfile**: o arquivo do Docker para aplicativos do ASP.NET Core se baseia na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="3f5e7-129">**Dockerfile**: the Docker file for ASP.NET Core applications is based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore) image.</span></span> <span data-ttu-id="3f5e7-130">Essa imagem inclui os pacotes NuGet do ASP.NET Core, que foram pré-compilados com JIT para melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-130">This image includes the ASP.NET Core NuGet packages, which have been pre-jitted improving startup performance.</span></span> <span data-ttu-id="3f5e7-131">Ao criar Aplicativos de Console do .NET Core, o Dockerfile FROM fará referência à imagem [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet) mais recente.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-131">When building .NET Core Console Applications, the Dockerfile FROM will reference the most recent [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet) image.</span></span>   
- <span data-ttu-id="3f5e7-132">**docker-compose.yml**: arquivo base do Docker Compose usado para definir o conjunto de imagens que serão compiladas e executadas com o build/execução do docker-compose.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-132">**docker-compose.yml**: base Docker Compose file used to define the collection of images to be built and run with docker-compose build/run.</span></span>   
- <span data-ttu-id="3f5e7-133">**docker-compose.dev.debug.yml**: arquivo docker-compose adicional com alterações iterativas quando a configuração está definida para depuração.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-133">**docker-compose.dev.debug.yml**: additional docker-compose file with for iterative changes when your configuration is set to debug.</span></span> <span data-ttu-id="3f5e7-134">O Visual Studio chamará -f docker-compose.yml -f docker-compose.dev.debug.yml para mesclá-los.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-134">Visual Studio will call -f docker-compose.yml -f docker-compose.dev.debug.yml to merge these together.</span></span> <span data-ttu-id="3f5e7-135">Esse arquivo de composição é usado pelas ferramentas de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-135">This compose file is used by Visual Studio development tools.</span></span>   
- <span data-ttu-id="3f5e7-136">**docker-compose.dev.release.yml**: arquivo adicional do Docker Compose para depurar sua definição de versão.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-136">**docker-compose.dev.release.yml**: additional Docker Compose file to debug your release definition.</span></span> <span data-ttu-id="3f5e7-137">Ele montará o volume do depurador, portanto ele não altera o conteúdo da imagem de produção.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-137">It will volume mount the debugger so it doesn't change the contents of the production image.</span></span>  

<span data-ttu-id="3f5e7-138">O arquivo *docker-compose.yml* contém o nome da imagem que é criada quando o projeto é executado.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-138">The *docker-compose.yml* file contains the name of the image that is created when project is run.</span></span> 

```
version '2'

services:
  hellodockertools:
    image:  user/hellodockertools${TAG}
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "80"
``` 

<span data-ttu-id="3f5e7-139">Neste exemplo, `image: user/hellodockertools${TAG}` gera a imagem `user/hellodockertools:dev` quando o aplicativo é executado no modo de **Depuração** e `user/hellodockertools:latest` no modo de **Lançamento**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-139">In this example, `image: user/hellodockertools${TAG}` generates the image `user/hellodockertools:dev` when the application is run in **Debug** mode and `user/hellodockertools:latest` in **Release** mode respectively.</span></span> 

<span data-ttu-id="3f5e7-140">Você deve alterar o `user` para seu nome de usuário do [Hub do Docker](https://hub.docker.com/) se planejar enviar a imagem por push para o registro.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-140">You will want to change the `user` to your [Docker Hub](https://hub.docker.com/) username if you plan to push the image to the registry.</span></span> <span data-ttu-id="3f5e7-141">Por exemplo, `spboyer/hellodockertools`, ou altere para a URL do seu registro privado `privateregistry.domain.com/`, dependendo da configuração.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-141">For example, `spboyer/hellodockertools`, or change to your private registry URL `privateregistry.domain.com/` depending on your configuration.</span></span>

### <a name="debugging"></a><span data-ttu-id="3f5e7-142">Depuração</span><span class="sxs-lookup"><span data-stu-id="3f5e7-142">Debugging</span></span>

<span data-ttu-id="3f5e7-143">Selecione **Docker** no menu suspenso de depuração na barra de ferramentas e use F5 para iniciar a depuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-143">Select **Docker** from the debug drop-down in the toolbar and use F5 to start debugging the application.</span></span> 

- <span data-ttu-id="3f5e7-144">A imagem do *microsoft/aspnetcore* é adquirida (se ainda não estiver em seu cache)</span><span class="sxs-lookup"><span data-stu-id="3f5e7-144">The *microsoft/aspnetcore* image is acquired (if not already in your cache)</span></span>
- <span data-ttu-id="3f5e7-145">*ASPNETCORE_ENVIRONMENT* é definido como Desenvolvimento dentro do contêiner</span><span class="sxs-lookup"><span data-stu-id="3f5e7-145">*ASPNETCORE_ENVIRONMENT* is set to Development within the container</span></span>
- <span data-ttu-id="3f5e7-146">A PORTA 80 é EXPOSTA e mapeada para uma porta atribuída dinamicamente para o localhost.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-146">PORT 80 is EXPOSED and mapped to a dynamically assigned port for localhost.</span></span> <span data-ttu-id="3f5e7-147">A porta é determinada pelo host do docker e pode ser consultada com o docker ps.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-147">The port is determined by the docker host and can be queried with docker ps.</span></span> 
- <span data-ttu-id="3f5e7-148">Seu aplicativo é copiado para o contêiner</span><span class="sxs-lookup"><span data-stu-id="3f5e7-148">Your application is copied to the container</span></span>
- <span data-ttu-id="3f5e7-149">O navegador padrão é iniciado com o depurador anexado ao contêiner, usando a porta atribuída dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-149">Default browser is launched with the debugger attached to the container, using the dynamically assigned port.</span></span> 

<span data-ttu-id="3f5e7-150">A imagem criada resultante do Docker é a imagem de *desenvolvimento* do seu aplicativo com as imagens *microsoft/aspnetcore* como a imagem base.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-150">The resulting Docker image built is the *dev* image of your application with the *microsoft/aspnetcore* images as the base image.</span></span>

<span data-ttu-id="3f5e7-151">**Observação:** a imagem de desenvolvimento não inclui o conteúdo do aplicativo, pois as configurações de Depuração usam montagem de volume para fornecer uma experiência iterativa.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-151">**Note:** The dev image is empty of your app contents as Debug configurations use volume mounting to provide the iterative experience.</span></span> <span data-ttu-id="3f5e7-152">Para enviar uma imagem por push, use a configuração de Lançamento.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-152">To push an image, use the Release configuration.</span></span>

```console
REPOSITORY                  TAG         IMAGE ID            CREATED         SIZE
spboyer/hellodockertools    dev         0b6e2e44b3df        4 minutes ago   268.9 MB
microsoft/aspnetcore        1.0.1       189ad4312ce7        5 days ago      268.9 MB
```

<span data-ttu-id="3f5e7-153">O aplicativo é executado usando o contêiner que pode ser visto executando o comando `docker ps`.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-153">The application is running using the container, which you can see by running the `docker ps` command.</span></span>

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   4 minutes ago       Up 4 minutes        0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

### <a name="edit-and-continue"></a><span data-ttu-id="3f5e7-154">Editar e continuar</span><span class="sxs-lookup"><span data-stu-id="3f5e7-154">Edit and Continue</span></span>

<span data-ttu-id="3f5e7-155">Alterações em arquivos estáticos e/ou arquivos de modelo do razor (*.cshtml*) são atualizadas automaticamente sem a necessidade de uma etapa de compilação.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-155">Changes to static files and/or razor template files (*.cshtml*) are automatically updated without the need of a compilation step.</span></span> <span data-ttu-id="3f5e7-156">Faça a alteração, salve e toque em Atualizar no navegador para exibir a atualização.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-156">Make the change, save, and tap refresh in the browser to view the update.</span></span>  

<span data-ttu-id="3f5e7-157">Modificações em arquivos de código exigem a compilação e a reinicialização do Kestrel dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-157">Modifications to code files require compiling and a restart of Kestrel within the container.</span></span> <span data-ttu-id="3f5e7-158">Depois de fazer a alteração, use CTRL + F5 para executar o processo e iniciar o aplicativo dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-158">After making the change, use CTRL + F5 to perform the process and start the application within the container.</span></span> <span data-ttu-id="3f5e7-159">O contêiner Docker não é recriado ou interrompido; usando `docker ps` na linha de comando, você pode ver que o contêiner original ainda está em execução a partir de 10 minutos atrás.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-159">The Docker container is not rebuilt or stopped; using `docker ps` in the command line, you can see that the original container is still running as of 10 minutes ago.</span></span> 

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   10 minutes ago      Up 10 minutes       0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

### <a name="publishing-docker-images"></a><span data-ttu-id="3f5e7-160">Publicando imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="3f5e7-160">Publishing Docker images</span></span>

<span data-ttu-id="3f5e7-161">Depois de ter concluído o ciclo de desenvolvimento e depuração do seu aplicativo, o Ferramentas do Visual Studio para Docker ajudará você a criar a imagem de produção do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-161">Once you have completed the develop and debug cycle of your application, the Visual Studio Tools for Docker will help you create the production image of your application.</span></span> <span data-ttu-id="3f5e7-162">Altere o menu suspenso de depuração para **Lançamento** e compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-162">Change the debug dropdown to **Release** and build the application.</span></span> <span data-ttu-id="3f5e7-163">A ferramenta produzirá a imagem com o marcador `:latest` que você pode enviar por push para seu Registro privado ou Hub do Docker.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-163">The tooling will produce the image with the `:latest` tag which you can push to your private registry or Docker Hub.</span></span> 

<span data-ttu-id="3f5e7-164">Usando o comando `docker images`, você pode ver a lista de imagens.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-164">Using the `docker images` command, you can see the list of images.</span></span>

```console
REPOSITORY                 TAG                 IMAGE ID            CREATED             SIZE
spboyer/hellodockertools   latest              8184ae38ba91        5 seconds ago       278.4 MB
spboyer/hellodockertools   dev                 0b6e2e44b3df        About an hour ago   268.9 MB
microsoft/aspnetcore       1.0.1               189ad4312ce7        5 days ago          268.9 MB
```

<span data-ttu-id="3f5e7-165">Pode haver uma expectativa para a imagem de produção ou de lançamento serem menores em comparação à imagem de **desenvolvimento**; no entanto, com o uso do mapeamento de volume, o depurador e o aplicativo realmente foram executados em seu computador local e não dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-165">There may be an expectation for the production or release image to be smaller in size by comparison to the **dev** image; however, through the use of the volume mapping, the debugger and application were actually being run from your local machine and not within the container.</span></span> <span data-ttu-id="3f5e7-166">A imagem **mais recente** empacotou todo o código de aplicativo necessário para executar o aplicativo em um computador host, portanto, o delta é do tamanho do código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f5e7-166">The **latest** image has packaged the entire application code needed to run the application on a host machine, therefore the delta is the size of your application code.</span></span>