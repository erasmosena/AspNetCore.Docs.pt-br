---
title: "O programa de instalação do Microsoft Account logon externo"
author: rick-anderson
description: "Este tutorial demonstra a integração da autenticação de usuário de conta da Microsoft em um aplicativo existente do ASP.NET Core."
keywords: "ASP.NET Core, a conta da Microsoft, login, autenticação"
ms.author: riande
manager: wpickett
ms.date: 08/24/2017
ms.topic: article
ms.assetid: 66DB4B94-C78C-4005-BA03-3D982B87C268
ms.technology: aspnet
ms.prod: asp.net-core
uid: security/authentication/microsoft-logins
ms.openlocfilehash: 77c16e3ae93c9bfe1f569d0a5888c5b765d04241
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2017
---
# <a name="configuring-microsoft-account-authentication"></a><span data-ttu-id="c2bc6-104">Configurar a autenticação do Microsoft Account</span><span class="sxs-lookup"><span data-stu-id="c2bc6-104">Configuring Microsoft Account authentication</span></span>

<span data-ttu-id="c2bc6-105">Por [Valeriy Novytskyy](https://github.com/01binary) e [Rick Anderson](https://twitter.com/RickAndMSFT)</span><span class="sxs-lookup"><span data-stu-id="c2bc6-105">By [Valeriy Novytskyy](https://github.com/01binary) and [Rick Anderson](https://twitter.com/RickAndMSFT)</span></span>

<span data-ttu-id="c2bc6-106">Este tutorial mostra como habilitar os usuários entrar com sua conta da Microsoft usando um projeto do ASP.NET Core 2.0 de exemplo criado no [página anterior](index.md).</span><span class="sxs-lookup"><span data-stu-id="c2bc6-106">This tutorial shows you how to enable your users to sign in with their Microsoft account using a sample ASP.NET Core 2.0 project created on the [previous page](index.md).</span></span>

## <a name="create-the-app-in-microsoft-developer-portal"></a><span data-ttu-id="c2bc6-107">Criar o aplicativo no Portal do desenvolvedor da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2bc6-107">Create the app in Microsoft Developer Portal</span></span>

* <span data-ttu-id="c2bc6-108">Navegue até [https://apps.dev.microsoft.com](https://apps.dev.microsoft.com) e criar ou entrar em uma conta da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-108">Navigate to [https://apps.dev.microsoft.com](https://apps.dev.microsoft.com) and create or sign into a Microsoft account:</span></span>

![Entrar na caixa de diálogo](index/_static/MicrosoftDevLogin.png)

<span data-ttu-id="c2bc6-110">Se você ainda não tiver uma conta da Microsoft, toque em  **[criar um!](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=13&ct=1478151035&rver=6.7.6643.0&wp=SAPI_LONG&wreply=https%3a%2f%2fapps.dev.microsoft.com%2fLoginPostBack&id=293053&aadredir=1&contextid=D70D4F21246BAB50&bk=1478151036&uiflavor=web&uaid=f0c3de863a914c358b8dc01b1ff49e85&mkt=EN-US&lc=1033&lic=1)**</span><span class="sxs-lookup"><span data-stu-id="c2bc6-110">If you don't already have a Microsoft account, tap **[Create one!](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=13&ct=1478151035&rver=6.7.6643.0&wp=SAPI_LONG&wreply=https%3a%2f%2fapps.dev.microsoft.com%2fLoginPostBack&id=293053&aadredir=1&contextid=D70D4F21246BAB50&bk=1478151036&uiflavor=web&uaid=f0c3de863a914c358b8dc01b1ff49e85&mkt=EN-US&lc=1033&lic=1)**</span></span> <span data-ttu-id="c2bc6-111">Depois de entrar, você será redirecionado para **meus aplicativos** página:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-111">After signing in you are redirected to **My applications** page:</span></span>

![Portal do desenvolvedor do Microsoft aberto no Microsoft Edge](index/_static/MicrosoftDev.png)

* <span data-ttu-id="c2bc6-113">Toque em **adicionar um aplicativo** no canto superior direito de canto e insira seu **nome do aplicativo** e **Contact Email**:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-113">Tap **Add an app** in the upper right corner and enter your **Application Name** and **Contact Email**:</span></span>

![Caixa de diálogo Nova registro de aplicativo](index/_static/MicrosoftDevAppCreate.png)

* <span data-ttu-id="c2bc6-115">Para os fins deste tutorial, desmarque o **instalação interativa** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-115">For the purposes of this tutorial, clear the **Guided Setup** check box.</span></span>

* <span data-ttu-id="c2bc6-116">Toque em **criar** para continuar a **registro** página.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-116">Tap **Create** to continue to the **Registration** page.</span></span> <span data-ttu-id="c2bc6-117">Forneça um **nome** e observe o valor da **Id do aplicativo**, que você usar como `ClientId` posteriormente no tutorial:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-117">Provide a **Name** and note the value of the **Application Id**, which you use as `ClientId` later in the tutorial:</span></span>

![Página de registro](index/_static/MicrosoftDevAppReg.png)

* <span data-ttu-id="c2bc6-119">Toque em **Adicionar plataforma** no **plataformas** seção e selecione o **Web** plataforma:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-119">Tap **Add Platform** in the **Platforms** section and select the **Web** platform:</span></span>

![Adicionar caixa de diálogo de plataforma](index/_static/MicrosoftDevAppPlatform.png)

* <span data-ttu-id="c2bc6-121">No novo **Web** plataforma seção, digite a URL de desenvolvimento com */signin-microsoft* acrescentados no **URLs de redirecionamento** campo (por exemplo: `https://localhost:44320/signin-microsoft`).</span><span class="sxs-lookup"><span data-stu-id="c2bc6-121">In the new **Web** platform section, enter your development URL with */signin-microsoft* appended into the **Redirect URLs** field (for example: `https://localhost:44320/signin-microsoft`).</span></span> <span data-ttu-id="c2bc6-122">O esquema de autenticação da Microsoft configurado mais tarde neste tutorial automaticamente manipulará as solicitações no */signin-microsoft* rota para implementar o fluxo de OAuth:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-122">The Microsoft authentication scheme configured later in this tutorial will automatically handle requests at */signin-microsoft* route to implement the OAuth flow:</span></span>

![Seção de plataforma da Web](index/_static/MicrosoftRedirectUri.png)

* <span data-ttu-id="c2bc6-124">Toque em **Adicionar URL** para garantir que a URL foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-124">Tap **Add URL** to ensure the URL was added.</span></span>

* <span data-ttu-id="c2bc6-125">Preencha quaisquer outras configurações de aplicativo, se necessário e toque em **salvar** na parte inferior da página para salvar as alterações de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-125">Fill out any other application settings if necessary and tap **Save** at the bottom of the page to save changes to app configuration.</span></span>

* <span data-ttu-id="c2bc6-126">Ao implantar o site será necessário rever o **registro** página e defina uma nova URL pública.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-126">When deploying the site you'll need to revisit the **Registration** page and set a new public URL.</span></span>

## <a name="store-microsoft-application-id-and-password"></a><span data-ttu-id="c2bc6-127">Armazenar a Id do aplicativo da Microsoft e a senha</span><span class="sxs-lookup"><span data-stu-id="c2bc6-127">Store Microsoft Application Id and Password</span></span>

* <span data-ttu-id="c2bc6-128">Observe o `Application Id` exibido no **registro** página.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-128">Note the `Application Id` displayed on the **Registration** page.</span></span>

* <span data-ttu-id="c2bc6-129">Toque em **gerar nova senha** no **segredos do aplicativo** seção.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-129">Tap **Generate New Password** in the **Application Secrets** section.</span></span> <span data-ttu-id="c2bc6-130">Isso exibe uma caixa em que você pode copiar a senha de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-130">This displays a box where you can copy the application password:</span></span>

![Caixa de diálogo Nova senha gerada](index/_static/MicrosoftDevPassword.png)

<span data-ttu-id="c2bc6-132">Vincular as configurações confidenciais como Microsoft `Application ID` e `Password` para sua configuração de aplicativo usando o [Manager segredo](../../app-secrets.md).</span><span class="sxs-lookup"><span data-stu-id="c2bc6-132">Link sensitive settings like Microsoft `Application ID` and `Password` to your application configuration using the [Secret Manager](../../app-secrets.md).</span></span> <span data-ttu-id="c2bc6-133">Para os fins deste tutorial, nomeie os tokens `Authentication:Microsoft:ApplicationId` e `Authentication:Microsoft:Password`.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-133">For the purposes of this tutorial, name the tokens `Authentication:Microsoft:ApplicationId` and `Authentication:Microsoft:Password`.</span></span>

## <a name="configure-microsoft-account-authentication"></a><span data-ttu-id="c2bc6-134">Configurar a autenticação de conta da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2bc6-134">Configure Microsoft Account Authentication</span></span>

<span data-ttu-id="c2bc6-135">O modelo de projeto usado neste tutorial garante que [Microsoft.AspNetCore.Authentication.MicrosoftAccount](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.MicrosoftAccount) pacote já está instalado.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-135">The project template used in this tutorial ensures that [Microsoft.AspNetCore.Authentication.MicrosoftAccount](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.MicrosoftAccount) package is already installed.</span></span>

* <span data-ttu-id="c2bc6-136">Para instalar este pacote com 2017 do Visual Studio, clique com botão direito no projeto e selecione **gerenciar pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-136">To install this package with Visual Studio 2017, right-click on the project and select **Manage NuGet Packages**.</span></span>
* <span data-ttu-id="c2bc6-137">Para instalar o .NET Core CLI, execute o seguinte no diretório do projeto:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-137">To install with .NET Core CLI, execute the following in your project directory:</span></span>

   `dotnet add package Microsoft.AspNetCore.Authentication.MicrosoftAccount`

# <a name="aspnet-core-2xtabaspnetcore2x"></a>[<span data-ttu-id="c2bc6-138">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c2bc6-138">ASP.NET Core 2.x</span></span>](#tab/aspnetcore2x)

<span data-ttu-id="c2bc6-139">Adicione o serviço Microsoft Account no `ConfigureServices` método *Startup.cs* arquivo:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-139">Add the Microsoft Account service in the `ConfigureServices` method in *Startup.cs* file:</span></span>

```csharp
services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();

services.AddAuthentication().AddMicrosoftAccount(microsoftOptions =>
{
    microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ApplicationId"];
    microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:Password"];
});
```

[!INCLUDE[default settings configuration](includes/default-settings.md)]

# <a name="aspnet-core-1xtabaspnetcore1x"></a>[<span data-ttu-id="c2bc6-140">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c2bc6-140">ASP.NET Core 1.x</span></span>](#tab/aspnetcore1x)

<span data-ttu-id="c2bc6-141">Adicionar o middleware Account da Microsoft no `Configure` método *Startup.cs* arquivo:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-141">Add the Microsoft Account middleware in the `Configure` method in *Startup.cs* file:</span></span>

```csharp
app.UseMicrosoftAccountAuthentication(new MicrosoftAccountOptions()
{
    ClientId = Configuration["Authentication:Microsoft:ApplicationId"],
    ClientSecret = Configuration["Authentication:Microsoft:Password"]
});
```

---

<span data-ttu-id="c2bc6-142">Embora a terminologia usada no Portal do desenvolvedor do Microsoft nomes esses tokens `ApplicationId` e `Password`, eles são expostos como `ClientId` e `ClientSecret` para a API de configuração.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-142">Although the terminology used on Microsoft Developer Portal names these tokens `ApplicationId` and `Password`, they are exposed as `ClientId` and `ClientSecret` to the configuration API.</span></span>

<span data-ttu-id="c2bc6-143">Consulte o [MicrosoftAccountOptions](https://docs.microsoft.com/aspnet/core/api/microsoft.aspnetcore.builder.microsoftaccountoptions) referência de API para obter mais informações sobre opções de configuração com suporte pela autenticação Account da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-143">See the [MicrosoftAccountOptions](https://docs.microsoft.com/aspnet/core/api/microsoft.aspnetcore.builder.microsoftaccountoptions) API reference for more information on configuration options supported by Microsoft Account authentication.</span></span> <span data-ttu-id="c2bc6-144">Isso pode ser usado para solicitar informações diferentes sobre o usuário.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-144">This can be used to request different information about the user.</span></span>

## <a name="sign-in-with-microsoft-account"></a><span data-ttu-id="c2bc6-145">Entrar com a conta da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2bc6-145">Sign in with Microsoft Account</span></span>

<span data-ttu-id="c2bc6-146">Execute o aplicativo e clique em **login**.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-146">Run your application and click **Log in**.</span></span> <span data-ttu-id="c2bc6-147">Uma opção para entrar com Microsoft será exibida:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-147">An option to sign in with Microsoft appears:</span></span>

![Log de aplicativo na página da Web: usuário não autenticado](index/_static/DoneMicrosoft.png)

<span data-ttu-id="c2bc6-149">Quando você clica na Microsoft, você é redirecionado para a Microsoft para autenticação.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-149">When you click on Microsoft, you are redirected to Microsoft for authentication.</span></span> <span data-ttu-id="c2bc6-150">Depois de entrar com sua Account da Microsoft (se ainda não estiver conectado), você será solicitado para permitir que o aplicativo acessar suas informações:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-150">After signing in with your Microsoft Account (if not already signed in) you will be prompted to let the app access your info:</span></span>

![Caixa de diálogo de autenticação Microsoft](index/_static/MicrosoftLogin.png)

<span data-ttu-id="c2bc6-152">Toque em **Sim** e você será redirecionado para o site da web onde você pode definir seu email.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-152">Tap **Yes** and you will be redirected back to the web site where you can set your email.</span></span>

<span data-ttu-id="c2bc6-153">Agora você está conectado usando suas credenciais da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="c2bc6-153">You are now logged in using your Microsoft credentials:</span></span>

![Aplicativo Web: usuário autenticado](index/_static/Done.png)

## <a name="troubleshooting"></a><span data-ttu-id="c2bc6-155">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c2bc6-155">Troubleshooting</span></span>

* <span data-ttu-id="c2bc6-156">Se o provedor do Microsoft Account redireciona para uma página de erro de entrada, observe os erro título e descrição de cadeia de caracteres parâmetros de consulta diretamente após o `#` (hashtag) no Uri.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-156">If the Microsoft Account provider redirects you to a sign in error page, note the error title and description query string parameters directly following the `#` (hashtag) in the Uri.</span></span>

  <span data-ttu-id="c2bc6-157">Embora a mensagem de erro parece ser um problema com a autenticação do Microsoft, a causa mais comum é seu aplicativo Uri não corresponde a nenhuma do **URIs de redirecionamento** especificado para o **Web** plataforma .</span><span class="sxs-lookup"><span data-stu-id="c2bc6-157">Although the error message seems to indicate a problem with Microsoft authentication, the most common cause is your application Uri not matching any of the **Redirect URIs** specified for the **Web** platform.</span></span>
* <span data-ttu-id="c2bc6-158">**ASP.NET Core 2. x somente:** identidade se não está configurada por meio da chamada `services.AddIdentity` na `ConfigureServices`, tentar autenticar resultará em *ArgumentException: A opção 'SignInScheme' deve ser fornecida*.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-158">**ASP.NET Core 2.x only:** If Identity is not configured by calling `services.AddIdentity` in `ConfigureServices`, attempting to authenticate will result in *ArgumentException: The 'SignInScheme' option must be provided*.</span></span> <span data-ttu-id="c2bc6-159">O modelo de projeto usado neste tutorial garante que isso é feito.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-159">The project template used in this tutorial ensures that this is done.</span></span>
* <span data-ttu-id="c2bc6-160">Se o banco de dados do site não tiver sido criado, aplicando a migração inicial, você obterá *uma operação de banco de dados falhou ao processar a solicitação* erro.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-160">If the site database has not been created by applying the initial migration, you will get *A database operation failed while processing the request* error.</span></span> <span data-ttu-id="c2bc6-161">Toque em **aplicar migrações** para criar o banco de dados e a atualização para continuar após o erro.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-161">Tap **Apply Migrations** to create the database and refresh to continue past the error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2bc6-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c2bc6-162">Next steps</span></span>

* <span data-ttu-id="c2bc6-163">Este artigo mostrou como você pode autenticar com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-163">This article showed how you can authenticate with Microsoft.</span></span> <span data-ttu-id="c2bc6-164">Você pode seguir uma abordagem semelhante para autenticar com outros provedores listados no [página anterior](index.md).</span><span class="sxs-lookup"><span data-stu-id="c2bc6-164">You can follow a similar approach to authenticate with other providers listed on the [previous page](index.md).</span></span>

* <span data-ttu-id="c2bc6-165">Depois de publicar seu site da web para o aplicativo web do Azure, você deve criar um novo `Password` no Portal do desenvolvedor do Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-165">Once you publish your web site to Azure web app, you should create a new `Password` in the Microsoft Developer Portal.</span></span>

* <span data-ttu-id="c2bc6-166">Definir o `Authentication:Microsoft:ApplicationId` e `Authentication:Microsoft:Password` como configurações de aplicativo no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-166">Set the `Authentication:Microsoft:ApplicationId` and `Authentication:Microsoft:Password` as application settings in the Azure portal.</span></span> <span data-ttu-id="c2bc6-167">O sistema de configuração é configurado para ler as chaves de variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="c2bc6-167">The configuration system is set up to read keys from environment variables.</span></span>