# <a name="aspnet-core-response-caching-sample"></a><span data-ttu-id="b2614-101">Exemplo de cache de resposta ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2614-101">ASP.NET Core Response Caching Sample</span></span>

<span data-ttu-id="b2614-102">Este exemplo ilustra o uso do [middleware de cache de resposta](https://docs.microsoft.com/aspnet/core/performance/caching/middleware)ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2614-102">This sample illustrates the usage of ASP.NET Core [Response Caching Middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware).</span></span>

<span data-ttu-id="b2614-103">O aplicativo responde com sua página de índice, incluindo `Cache-Control` um cabeçalho para configurar o comportamento de Caching.</span><span class="sxs-lookup"><span data-stu-id="b2614-103">The app responds with its Index page, including a `Cache-Control` header to configure caching behavior.</span></span> <span data-ttu-id="b2614-104">O aplicativo também define o `Vary` cabeçalho para configurar o cache para atender à resposta somente se o `Accept-Encoding` cabeçalho das solicitações subsequentes corresponder à solicitação original.</span><span class="sxs-lookup"><span data-stu-id="b2614-104">The app also sets the `Vary` header to configure the cache to serve the response only if the `Accept-Encoding` header of subsequent requests matches that from the original request.</span></span>

<span data-ttu-id="b2614-105">Ao executar o exemplo, a página de índice é servida do cache quando armazenada e armazenada em cache por até 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="b2614-105">When running the sample, the Index page is served from cache when stored and cached for up to 10 seconds.</span></span>

<span data-ttu-id="b2614-106">Para testar o comportamento de Caching:</span><span class="sxs-lookup"><span data-stu-id="b2614-106">To test caching behavior:</span></span>

* <span data-ttu-id="b2614-107">Não use um navegador para testar o comportamento do cache.</span><span class="sxs-lookup"><span data-stu-id="b2614-107">Don't use a browser to test caching behavior.</span></span> <span data-ttu-id="b2614-108">Os navegadores geralmente adicionam um cabeçalho de controle de cache ao recarregar, o que impede que o middleware forneça uma página armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="b2614-108">Browsers often add a cache control header on reload that prevent the middleware from serving a cached page.</span></span> <span data-ttu-id="b2614-109">Por exemplo, um `Cache-Control` cabeçalho com um valor de `max-age=0`) pode ser adicionado pelo navegador.</span><span class="sxs-lookup"><span data-stu-id="b2614-109">For example, a `Cache-Control` header with a value of `max-age=0`) might be added by the browser.</span></span>
* <span data-ttu-id="b2614-110">Use uma ferramenta de desenvolvedor que permita definir os cabeçalhos de solicitação explicitamente, como o <a href="https://www.telerik.com/fiddler">Fiddler</a> ou o <a href="https://www.getpostman.com/">postmaster</a>.</span><span class="sxs-lookup"><span data-stu-id="b2614-110">Use a developer tool that permits setting the request headers explicitly, such as <a href="https://www.telerik.com/fiddler">Fiddler</a> or <a href="https://www.getpostman.com/">Postman</a>.</span></span>