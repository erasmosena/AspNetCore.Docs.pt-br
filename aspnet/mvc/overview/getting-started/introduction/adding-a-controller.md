---
uid: mvc/overview/getting-started/introduction/adding-a-controller
title: Adicionando um controlador | Microsoft Docs
author: Rick-Anderson
description: 
ms.author: aspnetcontent
manager: wpickett
ms.date: 10/17/2013
ms.topic: article
ms.assetid: cc764f3b-6921-486a-8f44-c6ccd1249acd
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/getting-started/introduction/adding-a-controller
msc.type: authoredcontent
ms.openlocfilehash: 878d957344a08450b82b0249d8ca2a205810da4a
ms.sourcegitcommit: 9ecd4e9fb0c40c3693dab079eab1ff94b461c922
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
<a name="adding-a-controller"></a><span data-ttu-id="ce67b-102">Adicionando um controlador</span><span class="sxs-lookup"><span data-stu-id="ce67b-102">Adding a Controller</span></span>
====================
<span data-ttu-id="ce67b-103">Por [Rick Anderson](https://github.com/Rick-Anderson)</span><span class="sxs-lookup"><span data-stu-id="ce67b-103">by [Rick Anderson](https://github.com/Rick-Anderson)</span></span>

[!INCLUDE[Tutorial Note](sample/code-location.md)]

<span data-ttu-id="ce67b-104">Representa o MVC *model-view-controller*.</span><span class="sxs-lookup"><span data-stu-id="ce67b-104">MVC stands for *model-view-controller*.</span></span> <span data-ttu-id="ce67b-105">MVC é um padrão para o desenvolvimento de aplicativos que são bem projetada, podem ser testados e fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="ce67b-105">MVC is a pattern for developing applications that are well architected, testable and easy to maintain.</span></span> <span data-ttu-id="ce67b-106">Aplicativos MVC contêm:</span><span class="sxs-lookup"><span data-stu-id="ce67b-106">MVC-based applications contain:</span></span>

- <span data-ttu-id="ce67b-107">**M** odels: Classes que representam os dados do aplicativo e que usam a lógica de validação para impor regras de negócio para os dados.</span><span class="sxs-lookup"><span data-stu-id="ce67b-107">**M** odels: Classes that represent the data of the application and that use validation logic to enforce business rules for that data.</span></span>
- <span data-ttu-id="ce67b-108">**V** iews: arquivos de modelo que seu aplicativo usa para gerar dinamicamente as respostas HTML.</span><span class="sxs-lookup"><span data-stu-id="ce67b-108">**V** iews: Template files that your application uses to dynamically generate HTML responses.</span></span>
- <span data-ttu-id="ce67b-109">**C** ontrollers: Classes que lidam com solicitações recebidas de navegador, recuperar dados de modelo e, em seguida, especificar modelos de exibição que retornam uma resposta para o navegador.</span><span class="sxs-lookup"><span data-stu-id="ce67b-109">**C** ontrollers: Classes that handle incoming browser requests, retrieve model data, and then specify view templates that return a response to the browser.</span></span>

<span data-ttu-id="ce67b-110">Vamos ser abrangendo todos esses conceitos nesta série de tutoriais e mostram como usá-las para criar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce67b-110">We'll be covering all these concepts in this tutorial series and show you how to use them to build an application.</span></span>

> [!NOTE]
> <span data-ttu-id="ce67b-111">Na etapa anterior, o padrão MVC modelo foi selecionado.</span><span class="sxs-lookup"><span data-stu-id="ce67b-111">In the previous step the Default MVC template was selected.</span></span> <span data-ttu-id="ce67b-112">Isso cria Home, conta e gerenciar controladores por padrão.</span><span class="sxs-lookup"><span data-stu-id="ce67b-112">This creates Home, Account and Manage Controllers by default.</span></span>

<span data-ttu-id="ce67b-113">Vamos começar criando uma classe de controlador.</span><span class="sxs-lookup"><span data-stu-id="ce67b-113">Let's begin by creating a controller class.</span></span> <span data-ttu-id="ce67b-114">No **Gerenciador de soluções**, com o botão direito a *controladores* pasta e clique **adicionar**, em seguida, **controlador**.</span><span class="sxs-lookup"><span data-stu-id="ce67b-114">In **Solution Explorer**, right-click the *Controllers* folder and then click **Add**, then **Controller**.</span></span>


![](adding-a-controller/_static/image1.png)

<span data-ttu-id="ce67b-115">No **adicionar Scaffold** caixa de diálogo, clique em **controlador MVC 5 - vazio**e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ce67b-115">In the **Add Scaffold** dialog box, click **MVC 5 Controller - Empty**, and then click **Add**.</span></span>

![](adding-a-controller/_static/image2.png)  
 

<span data-ttu-id="ce67b-116">Nomeie o novo controlador de "HelloWorldController" e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ce67b-116">Name your new controller "HelloWorldController" and click **Add**.</span></span>

![Adicionar controlador](adding-a-controller/_static/image3.png)

<span data-ttu-id="ce67b-118">Observe na **Solution Explorer** que um novo arquivo tem foi criado com o nome *HelloWorldController.cs* e uma nova pasta *Views\HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="ce67b-118">Notice in **Solution Explorer** that a new file has been created named *HelloWorldController.cs* and a new folder *Views\HelloWorld*.</span></span> <span data-ttu-id="ce67b-119">O controlador está aberto no IDE.</span><span class="sxs-lookup"><span data-stu-id="ce67b-119">The controller is open in the IDE.</span></span>

![](adding-a-controller/_static/image4.png)

<span data-ttu-id="ce67b-120">Substitua o conteúdo do arquivo com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ce67b-120">Replace the contents of the file with the following code.</span></span>

[!code-csharp[Main](adding-a-controller/samples/sample1.cs)]

<span data-ttu-id="ce67b-121">Os métodos do controlador retornará uma cadeia de caracteres de HTML como um exemplo.</span><span class="sxs-lookup"><span data-stu-id="ce67b-121">The controller methods will return a string of HTML as an example.</span></span> <span data-ttu-id="ce67b-122">O controlador é nomeado `HelloWorldController` e o primeiro método é chamado `Index`.</span><span class="sxs-lookup"><span data-stu-id="ce67b-122">The controller is named `HelloWorldController` and the first method is named `Index`.</span></span> <span data-ttu-id="ce67b-123">Vamos chamá-la em um navegador.</span><span class="sxs-lookup"><span data-stu-id="ce67b-123">Let's invoke it from a browser.</span></span> <span data-ttu-id="ce67b-124">Execute o aplicativo (pressione F5 ou Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="ce67b-124">Run the application (press F5 or Ctrl+F5).</span></span> <span data-ttu-id="ce67b-125">No navegador, acrescente &quot;HelloWorld&quot; para o caminho na barra de endereços.</span><span class="sxs-lookup"><span data-stu-id="ce67b-125">In the browser, append &quot;HelloWorld&quot; to the path in the address bar.</span></span> <span data-ttu-id="ce67b-126">(Por exemplo, na ilustração abaixo, ele `http://localhost:1234/HelloWorld.`) a página no navegador se parecerá com a captura de tela a seguir.</span><span class="sxs-lookup"><span data-stu-id="ce67b-126">(For example, in the illustration below, it's `http://localhost:1234/HelloWorld.`) The page in the browser will look like the following screenshot.</span></span> <span data-ttu-id="ce67b-127">No método, o código retornado diretamente uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ce67b-127">In the method above, the code returned a string directly.</span></span> <span data-ttu-id="ce67b-128">Você disse que o sistema retornar apenas alguns HTML e fez isso!</span><span class="sxs-lookup"><span data-stu-id="ce67b-128">You told the system to just return some HTML, and it did!</span></span>

![](adding-a-controller/_static/image5.png)

<span data-ttu-id="ce67b-129">ASP.NET MVC chama classes diferentes de controlador (e os métodos de ação diferente dentro delas) dependendo da URL de entrada.</span><span class="sxs-lookup"><span data-stu-id="ce67b-129">ASP.NET MVC invokes different controller classes (and different action methods within them) depending on the incoming URL.</span></span> <span data-ttu-id="ce67b-130">A lógica de roteamento URL padrão usada pelo ASP.NET MVC usa um formato como este para determinar o que o código para chamar:</span><span class="sxs-lookup"><span data-stu-id="ce67b-130">The default URL routing logic used by ASP.NET MVC uses a format like this to determine what code to invoke:</span></span>

`/[Controller]/[ActionName]/[Parameters]`

<span data-ttu-id="ce67b-131">Você define o formato de roteamento de *aplicativo\_Start/RouteConfig.cs* arquivo.</span><span class="sxs-lookup"><span data-stu-id="ce67b-131">You set the format for routing in the *App\_Start/RouteConfig.cs* file.</span></span>

[!code-csharp[Main](adding-a-controller/samples/sample2.cs?highlight=7-8)]

<span data-ttu-id="ce67b-132">Quando você executa o aplicativo e não fornece qualquer segmentos de URL, o padrão é o controlador "Home" e o método de ação de "Index" especificado na seção de padrões de código acima.</span><span class="sxs-lookup"><span data-stu-id="ce67b-132">When you run the application and don't supply any URL segments, it defaults to the "Home" controller and the "Index" action method specified in the defaults section of the code above.</span></span>

<span data-ttu-id="ce67b-133">A primeira parte da URL determina a classe do controlador para executar.</span><span class="sxs-lookup"><span data-stu-id="ce67b-133">The first part of the URL determines the controller class to execute.</span></span> <span data-ttu-id="ce67b-134">Portanto */HelloWorld* mapeia para o `HelloWorldController` classe.</span><span class="sxs-lookup"><span data-stu-id="ce67b-134">So */HelloWorld* maps to the `HelloWorldController` class.</span></span> <span data-ttu-id="ce67b-135">A segunda parte da URL determina o método de ação na classe para executar.</span><span class="sxs-lookup"><span data-stu-id="ce67b-135">The second part of the URL determines the action method on the class to execute.</span></span> <span data-ttu-id="ce67b-136">Portanto *HelloWorld/índice* causaria o `Index` método o `HelloWorldController` classe para executar.</span><span class="sxs-lookup"><span data-stu-id="ce67b-136">So */HelloWorld/Index* would cause the `Index` method of the `HelloWorldController` class to execute.</span></span> <span data-ttu-id="ce67b-137">Observe que tivemos somente para navegar até */HelloWorld* e `Index` método foi usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ce67b-137">Notice that we only had to browse to */HelloWorld* and the `Index` method was used by default.</span></span> <span data-ttu-id="ce67b-138">Isso ocorre porque um método chamado `Index` é o método padrão que será chamado em um controlador, se ainda não for explicitamente especificado.</span><span class="sxs-lookup"><span data-stu-id="ce67b-138">This is because a method named `Index` is the default method that will be called on a controller if one is not explicitly specified.</span></span> <span data-ttu-id="ce67b-139">A terceira parte do segmento de URL (`Parameters`) refere-se aos dados de rota.</span><span class="sxs-lookup"><span data-stu-id="ce67b-139">The third part of the URL segment ( `Parameters`) is for route data.</span></span> <span data-ttu-id="ce67b-140">Veremos dados da rota mais tarde neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="ce67b-140">We'll see route data later on in this tutorial.</span></span>

<span data-ttu-id="ce67b-141">Navegue para `http://localhost:xxxx/HelloWorld/Welcome`.</span><span class="sxs-lookup"><span data-stu-id="ce67b-141">Browse to `http://localhost:xxxx/HelloWorld/Welcome`.</span></span> <span data-ttu-id="ce67b-142">O `Welcome` método é executado e retorna a cadeia de caracteres &quot;esse é o método de ação de boas-vindas... &quot;.</span><span class="sxs-lookup"><span data-stu-id="ce67b-142">The `Welcome` method runs and returns the string &quot;This is the Welcome action method...&quot;.</span></span> <span data-ttu-id="ce67b-143">O mapeamento de MVC padrão é `/[Controller]/[ActionName]/[Parameters]`.</span><span class="sxs-lookup"><span data-stu-id="ce67b-143">The default MVC mapping is `/[Controller]/[ActionName]/[Parameters]`.</span></span> <span data-ttu-id="ce67b-144">Para essa URL, o controlador é `HelloWorld` e `Welcome` é o método de ação.</span><span class="sxs-lookup"><span data-stu-id="ce67b-144">For this URL, the controller is `HelloWorld` and `Welcome` is the action method.</span></span> <span data-ttu-id="ce67b-145">Você ainda não usou a parte `[Parameters]` da URL.</span><span class="sxs-lookup"><span data-stu-id="ce67b-145">You haven't used the `[Parameters]` part of the URL yet.</span></span>

![](adding-a-controller/_static/image6.png)

<span data-ttu-id="ce67b-146">Vamos modificar o exemplo um pouco para que você pode passar algumas informações de parâmetro da URL para o controlador (por exemplo, *HelloWorld/boas-vindas? name = Scott&amp;numtimes = 4*).</span><span class="sxs-lookup"><span data-stu-id="ce67b-146">Let's modify the example slightly so that you can pass some parameter information from the URL to the controller (for example, */HelloWorld/Welcome?name=Scott&amp;numtimes=4*).</span></span> <span data-ttu-id="ce67b-147">Alterar sua `Welcome` método incluir dois parâmetros, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="ce67b-147">Change your `Welcome` method to include two parameters as shown below.</span></span> <span data-ttu-id="ce67b-148">Observe que o código usa o recurso de parâmetro opcional do c# para indicar que o `numTimes` parâmetro deve 1 como padrão se nenhum valor é passado para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ce67b-148">Note that the code uses the C# optional-parameter feature to indicate that the `numTimes` parameter should default to 1 if no value is passed for that parameter.</span></span>

[!code-csharp[Main](adding-a-controller/samples/sample3.cs)]

> [!NOTE]
> <span data-ttu-id="ce67b-149">Observação de segurança: O código acima usa [HttpUtility](https://msdn.microsoft.com/en-us/library/ee360286(v=vs.110).aspx) para proteger o aplicativo contra entrada mal-intencionada (ou seja, o JavaScript).</span><span class="sxs-lookup"><span data-stu-id="ce67b-149">Security Note: The code above uses [HttpUtility.HtmlEncode](https://msdn.microsoft.com/en-us/library/ee360286(v=vs.110).aspx) to protect the application from malicious input (namely JavaScript).</span></span> <span data-ttu-id="ce67b-150">Para obter mais informações, consulte [como: proteger contra scripts maliciosos em um aplicativo da Web aplicando codificação HTML a cadeias de caracteres](https://msdn.microsoft.com/en-us/library/a2a4yykt(v=vs.100).aspx).</span><span class="sxs-lookup"><span data-stu-id="ce67b-150">For more information see [How to: Protect Against Script Exploits in a Web Application by Applying HTML Encoding to Strings](https://msdn.microsoft.com/en-us/library/a2a4yykt(v=vs.100).aspx).</span></span>


 <span data-ttu-id="ce67b-151">Execute o aplicativo e navegue até a URL de exemplo (`http://localhost:xxxx/HelloWorld/Welcome?name=Scott&numtimes=4`).</span><span class="sxs-lookup"><span data-stu-id="ce67b-151">Run your application and browse to the example URL (`http://localhost:xxxx/HelloWorld/Welcome?name=Scott&numtimes=4`).</span></span> <span data-ttu-id="ce67b-152">Você pode tentar valores diferentes para `name` e `numtimes` na URL.</span><span class="sxs-lookup"><span data-stu-id="ce67b-152">You can try different values for `name` and `numtimes` in the URL.</span></span> <span data-ttu-id="ce67b-153">O [sistema de associação do ASP.NET MVC modelo](http://odetocode.com/Blogs/scott/archive/2009/04/27/6-tips-for-asp-net-mvc-model-binding.aspx) mapeia automaticamente os parâmetros nomeados da cadeia de consulta na barra de endereços para parâmetros em seu método.</span><span class="sxs-lookup"><span data-stu-id="ce67b-153">The [ASP.NET MVC model binding system](http://odetocode.com/Blogs/scott/archive/2009/04/27/6-tips-for-asp-net-mvc-model-binding.aspx) automatically maps the named parameters from the query string in the address bar to parameters in your method.</span></span>

![](adding-a-controller/_static/image7.png)

<span data-ttu-id="ce67b-154">No exemplo acima, o segmento de URL ( `Parameters`) não for usado, o `name` e `numTimes` parâmetros são passados como [cadeias de caracteres de consulta](http://en.wikipedia.org/wiki/Query_string).</span><span class="sxs-lookup"><span data-stu-id="ce67b-154">In the sample above, the URL segment ( `Parameters`) is not used, the `name` and `numTimes` parameters are passed as [query strings](http://en.wikipedia.org/wiki/Query_string).</span></span> <span data-ttu-id="ce67b-155">O caractere curinga ?</span><span class="sxs-lookup"><span data-stu-id="ce67b-155">The ?</span></span> <span data-ttu-id="ce67b-156">(ponto de interrogação) na URL acima é um separador e siga as cadeias de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="ce67b-156">(question mark) in the above URL is a separator, and the query strings follow.</span></span> <span data-ttu-id="ce67b-157">O caractere &amp; separa as cadeias de consulta.</span><span class="sxs-lookup"><span data-stu-id="ce67b-157">The &amp; character separates query strings.</span></span>

<span data-ttu-id="ce67b-158">Substitua o método de boas-vindo com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ce67b-158">Replace the Welcome method with the following code:</span></span>

[!code-csharp[Main](adding-a-controller/samples/sample4.cs)]

<span data-ttu-id="ce67b-159">Execute o aplicativo e digite a seguinte URL:`http://localhost:xxx/HelloWorld/Welcome/1?name=Scott`</span><span class="sxs-lookup"><span data-stu-id="ce67b-159">Run the application and enter the following URL: `http://localhost:xxx/HelloWorld/Welcome/1?name=Scott`</span></span>

![](adding-a-controller/_static/image8.png)

<span data-ttu-id="ce67b-160">Neste momento, o terceiro segmento de URL corresponde o parâmetro de rota `ID.` o `Welcome` método de ação contém um parâmetro (`ID`) que corresponde a especificação de URL no `RegisterRoutes` método.</span><span class="sxs-lookup"><span data-stu-id="ce67b-160">This time the third URL segment matched the route parameter `ID.` The `Welcome` action method contains a parameter (`ID`) that matched the URL specification in the `RegisterRoutes` method.</span></span>

[!code-csharp[Main](adding-a-controller/samples/sample5.cs?highlight=7)]

<span data-ttu-id="ce67b-161">Em aplicativos ASP.NET MVC, é mais comum para passar parâmetros como dados de rota (como fizemos com ID acima) que transmiti-los como cadeias de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="ce67b-161">In ASP.NET MVC applications, it's more typical to pass in parameters as route data (like we did with ID above) than passing them as query strings.</span></span> <span data-ttu-id="ce67b-162">Você também pode adicionar uma rota para passar ambos o `name` e `numtimes` em parâmetros como dados de rota na URL.</span><span class="sxs-lookup"><span data-stu-id="ce67b-162">You could also add a route to pass both the `name` and `numtimes` in parameters as route data in the URL.</span></span> <span data-ttu-id="ce67b-163">No *aplicativo\_Start\RouteConfig.cs* de arquivo, adicione a rota "Hello":</span><span class="sxs-lookup"><span data-stu-id="ce67b-163">In the *App\_Start\RouteConfig.cs* file, add the "Hello" route:</span></span>

[!code-csharp[Main](adding-a-controller/samples/sample6.cs?highlight=13-16)]

<span data-ttu-id="ce67b-164">Execute o aplicativo e navegue até `/localhost:XXX/HelloWorld/Welcome/Scott/3`.</span><span class="sxs-lookup"><span data-stu-id="ce67b-164">Run the application and browse to `/localhost:XXX/HelloWorld/Welcome/Scott/3`.</span></span>

![](adding-a-controller/_static/image9.png)

<span data-ttu-id="ce67b-165">Para muitos aplicativos MVC, a rota padrão funciona bem.</span><span class="sxs-lookup"><span data-stu-id="ce67b-165">For many MVC applications, the default route works fine.</span></span> <span data-ttu-id="ce67b-166">Você aprenderá mais tarde neste tutorial para passar dados usando o associador de modelo, e você não precisará modificar a rota padrão para que.</span><span class="sxs-lookup"><span data-stu-id="ce67b-166">You'll learn later in this tutorial to pass data using the model binder, and you won't have to modify the default route for that.</span></span>

<span data-ttu-id="ce67b-167">Nestes exemplos o controlador está executando o &quot;VC&quot; parte do MVC — ou seja, o trabalho de exibição e controlador.</span><span class="sxs-lookup"><span data-stu-id="ce67b-167">In these examples the controller has been doing the &quot;VC&quot; portion of MVC — that is, the view and controller work.</span></span> <span data-ttu-id="ce67b-168">O controlador está retornando HTML diretamente.</span><span class="sxs-lookup"><span data-stu-id="ce67b-168">The controller is returning HTML directly.</span></span> <span data-ttu-id="ce67b-169">Normalmente, você não deseja controladores retornando HTML diretamente, desde que se torna muito difícil de código.</span><span class="sxs-lookup"><span data-stu-id="ce67b-169">Ordinarily you don't want controllers returning HTML directly, since that becomes very cumbersome to code.</span></span> <span data-ttu-id="ce67b-170">Em vez disso, usaremos normalmente um arquivo de modelo de exibição separada para ajudar a gerar a resposta HTML.</span><span class="sxs-lookup"><span data-stu-id="ce67b-170">Instead we'll typically use a separate view template file to help generate the HTML response.</span></span> <span data-ttu-id="ce67b-171">Vamos Avançar como podemos fazer isso.</span><span class="sxs-lookup"><span data-stu-id="ce67b-171">Let's look next at how we can do this.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="ce67b-172">[Anterior](getting-started.md)
[Próximo](adding-a-view.md)</span><span class="sxs-lookup"><span data-stu-id="ce67b-172">[Previous](getting-started.md)
[Next](adding-a-view.md)</span></span>