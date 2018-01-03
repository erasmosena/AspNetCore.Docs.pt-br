---
uid: web-forms/overview/getting-started/getting-started-with-aspnet-45-web-forms/display_data_items_and_details
title: Exibir dados de itens e detalhes | Microsoft Docs
author: Erikre
description: "Esta série de tutorial irá ensiná-lo as Noções básicas de criação de um aplicativo de Web Forms do ASP.NET usando o ASP.NET 4.5 e o Microsoft Visual Studio Express 2013 para nós..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 09/08/2014
ms.topic: article
ms.assetid: 64a491a8-0ed6-4c2f-9c1c-412962eb6006
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/getting-started/getting-started-with-aspnet-45-web-forms/display_data_items_and_details
msc.type: authoredcontent
ms.openlocfilehash: 809d7a9c21a3ddf5dfd07d079eb8fe0d1d81712d
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2017
---
<a name="display-data-items-and-details"></a><span data-ttu-id="0e1b9-103">Exibir dados de itens e detalhes</span><span class="sxs-lookup"><span data-stu-id="0e1b9-103">Display Data Items and Details</span></span>
====================
<span data-ttu-id="0e1b9-104">Por [Erik Reitan](https://github.com/Erikre)</span><span class="sxs-lookup"><span data-stu-id="0e1b9-104">by [Erik Reitan](https://github.com/Erikre)</span></span>

<span data-ttu-id="0e1b9-105">[Baixe o projeto de exemplo do Wingtip Toys (c#)](http://go.microsoft.com/fwlink/?LinkID=389434&clcid=0x409) ou [baixar livro eletrônico (PDF)](http://download.microsoft.com/download/0/F/B/0FBFAA46-2BFD-478F-8E56-7BF3C672DF9D/Getting%20Started%20with%20ASP.NET%204.5%20Web%20Forms%20and%20Visual%20Studio%202013.pdf)</span><span class="sxs-lookup"><span data-stu-id="0e1b9-105">[Download Wingtip Toys Sample Project (C#)](http://go.microsoft.com/fwlink/?LinkID=389434&clcid=0x409) or [Download E-book (PDF)](http://download.microsoft.com/download/0/F/B/0FBFAA46-2BFD-478F-8E56-7BF3C672DF9D/Getting%20Started%20with%20ASP.NET%204.5%20Web%20Forms%20and%20Visual%20Studio%202013.pdf)</span></span>

> <span data-ttu-id="0e1b9-106">Esta série de tutorial irá ensiná-lo as Noções básicas de criação de um aplicativo de Web Forms do ASP.NET usando o ASP.NET 4.5 e o Microsoft Visual Studio Express 2013 para Web.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-106">This tutorial series will teach you the basics of building an ASP.NET Web Forms application using ASP.NET 4.5 and Microsoft Visual Studio Express 2013 for Web.</span></span> <span data-ttu-id="0e1b9-107">Um Visual Studio 2013 [projeto com o código-fonte c#](https://go.microsoft.com/fwlink/?LinkID=389434&clcid=0x409) está disponível para acompanhar esta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-107">A Visual Studio 2013 [project with C# source code](https://go.microsoft.com/fwlink/?LinkID=389434&clcid=0x409) is available to accompany this tutorial series.</span></span>


<span data-ttu-id="0e1b9-108">Este tutorial descreve como exibir itens de dados e detalhes de item de dados usando o Web Forms do ASP.NET e o Entity Framework Code First.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-108">This tutorial describes how to display data items and data item details using ASP.NET Web Forms and Entity Framework Code First.</span></span> <span data-ttu-id="0e1b9-109">Este tutorial se baseia no tutorial anterior "Da interface do usuário e a navegação" e é parte da série de tutorial da loja de brinquedos Wingtip.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-109">This tutorial builds on the previous tutorial "UI and Navigation" and is part of the Wingtip Toy Store tutorial series.</span></span> <span data-ttu-id="0e1b9-110">Depois de concluir este tutorial, você poderá ver os produtos no *ProductsList.aspx* página e detalhes sobre um produto individual no *ProductDetails.aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-110">When you've completed this tutorial, you'll be able to see products on the *ProductsList.aspx* page and details about an individual product on the *ProductDetails.aspx* page.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="0e1b9-111">O que você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-111">What you'll learn:</span></span>

- <span data-ttu-id="0e1b9-112">Como adicionar um controle de dados para exibir produtos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-112">How to add a data control to display products from the database.</span></span>
- <span data-ttu-id="0e1b9-113">Como se conectar a um controle de dados para os dados selecionados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-113">How to connect a data control to the selected data.</span></span>
- <span data-ttu-id="0e1b9-114">Como adicionar um controle de dados para exibir detalhes do produto do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-114">How to add a data control to display product details from the database.</span></span>
- <span data-ttu-id="0e1b9-115">Como recuperar um valor de cadeia de caracteres de consulta e use esse valor para limitar os dados recuperados do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-115">How to retrieve a value from the query string and use that value to limit the data that's retrieved from the database.</span></span>

### <a name="these-are-the-features-introduced-in-the-tutorial"></a><span data-ttu-id="0e1b9-116">Estes são os recursos apresentados no tutorial de:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-116">These are the features introduced in the tutorial:</span></span>

- <span data-ttu-id="0e1b9-117">Associação de modelo</span><span class="sxs-lookup"><span data-stu-id="0e1b9-117">Model Binding</span></span>
- <span data-ttu-id="0e1b9-118">Provedores de valor</span><span class="sxs-lookup"><span data-stu-id="0e1b9-118">Value providers</span></span>

## <a name="adding-a-data-control-to-display-products"></a><span data-ttu-id="0e1b9-119">Adicionando um controle de dados para exibir produtos</span><span class="sxs-lookup"><span data-stu-id="0e1b9-119">Adding a Data Control to Display Products</span></span>

<span data-ttu-id="0e1b9-120">Ao associar dados a um controle de servidor, há algumas opções diferentes, que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-120">When binding data to a server control, there are a few different options you can use.</span></span> <span data-ttu-id="0e1b9-121">As opções mais comuns incluem adicionando um controle de fonte de dados, adicionando o código manualmente ou usando a associação de modelo.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-121">The most common options include adding a data source control, adding code by hand, or using model binding.</span></span>

### <a name="using-a-data-source-control-to-bind-data"></a><span data-ttu-id="0e1b9-122">Usando um controle de fonte de dados para associar dados</span><span class="sxs-lookup"><span data-stu-id="0e1b9-122">Using a Data Source Control to Bind Data</span></span>

<span data-ttu-id="0e1b9-123">Adicionando um controle de fonte de dados permite que você vincular o controle de fonte de dados para o controle que exibe os dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-123">Adding a data source control allows you to link the data source control to the control that displays the data.</span></span> <span data-ttu-id="0e1b9-124">Essa abordagem permite a conexão declarativamente controles do lado do servidor diretamente a fontes de dados, em vez de usar uma abordagem programática.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-124">This approach allows you to declaratively connect server-side controls directly to data sources, rather than using a programmatic approach.</span></span>

### <a name="coding-by-hand-to-bind-data"></a><span data-ttu-id="0e1b9-125">Codificação manual para associar dados</span><span class="sxs-lookup"><span data-stu-id="0e1b9-125">Coding By Hand to Bind Data</span></span>

<span data-ttu-id="0e1b9-126">Adicionando código manualmente envolve ler o valor, procurando um valor nulo, tentar convertê-lo para o tipo apropriado, verificando se a conversão foi bem-sucedida e por fim, usando o valor na consulta.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-126">Adding code by hand involves reading the value, checking for a null value, attempting to convert it to the appropriate type, checking whether the conversion was successful, and finally, using the value in the query.</span></span> <span data-ttu-id="0e1b9-127">Você usaria essa abordagem quando você precisar manter controle total sobre a lógica de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-127">You would use this approach when you need to retain full control over your data-access logic.</span></span>

### <a name="using-model-binding-to-bind-data"></a><span data-ttu-id="0e1b9-128">Usando o modelo de associação para associar dados</span><span class="sxs-lookup"><span data-stu-id="0e1b9-128">Using Model Binding to Bind Data</span></span>

<span data-ttu-id="0e1b9-129">Usando a associação de modelo permite que você vincule os resultados usando muito menos código e oferece a capacidade de reutilizar a funcionalidade em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-129">Using model binding allows you to bind results using far less code and gives you the ability to reuse the functionality throughout your application.</span></span> <span data-ttu-id="0e1b9-130">Associação de modelo tem como objetivo para simplificar o trabalho com a lógica de acesso a dados focados no código enquanto ainda retém os benefícios de uma estrutura de vinculação de dados avançado.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-130">Model binding aims to simplify working with code-focused data-access logic while still retaining the benefits of a rich, data-binding framework.</span></span>

## <a name="displaying-products"></a><span data-ttu-id="0e1b9-131">Exibindo produtos</span><span class="sxs-lookup"><span data-stu-id="0e1b9-131">Displaying Products</span></span>

<span data-ttu-id="0e1b9-132">Neste tutorial, você usará a associação de modelo para associar dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-132">In this tutorial, you'll use model binding to bind data.</span></span> <span data-ttu-id="0e1b9-133">Para configurar um controle de dados para usar a associação de modelo para selecionar os dados, você define o controle `SelectMethod` propriedade para o nome de um método no código da página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-133">To configure a data control to use model binding to select data, you set the control's `SelectMethod` property to the name of a method in the page's code.</span></span> <span data-ttu-id="0e1b9-134">O controle de dados chama o método no momento apropriado no ciclo de vida da página e vincula automaticamente os dados retornados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-134">The data control calls the method at the appropriate time in the page life cycle and automatically binds the returned data.</span></span> <span data-ttu-id="0e1b9-135">Não é necessário chamar explicitamente o `DataBind` método.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-135">There's no need to explicitly call the `DataBind` method.</span></span>

<span data-ttu-id="0e1b9-136">Usando as etapas a seguir, você modificará a marcação no *ProductList. aspx* página para que a página pode exibir produtos.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-136">Using the steps below, you'll modify the markup in the *ProductList.aspx* page so that the page can display products.</span></span>

1. <span data-ttu-id="0e1b9-137">Em **Solution Explorer**, abra o *ProductList. aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-137">In **Solution Explorer**, open the *ProductList.aspx* page.</span></span>
2. <span data-ttu-id="0e1b9-138">Substitua a marcação existente com a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-138">Replace the existing markup with the following markup:</span></span>   

    [!code-aspx[Main](display_data_items_and_details/samples/sample1.aspx)]

<span data-ttu-id="0e1b9-139">Esse código usa um **ListView** controle chamado "verificação" para exibir os produtos.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-139">This code uses a **ListView** control named "productList" to display the products.</span></span>

[!code-aspx[Main](display_data_items_and_details/samples/sample2.aspx)]

<span data-ttu-id="0e1b9-140">O **ListView** controle exibe dados em um formato que você define usando modelos e estilos.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-140">The **ListView** control displays data in a format that you define by using templates and styles.</span></span> <span data-ttu-id="0e1b9-141">É útil para dados em qualquer estrutura de repetição.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-141">It is useful for data in any repeating structure.</span></span> <span data-ttu-id="0e1b9-142">Isso **ListView** exemplo simplesmente mostra dados de banco de dados, no entanto, você pode habilitar usuários para editar, inserir e excluir dados e para classificar e dados da página, tudo sem código.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-142">This **ListView** example simply shows data from the database, however you can enable users to edit, insert, and delete data, and to sort and page data, all without code.</span></span>

<span data-ttu-id="0e1b9-143">Definindo o `ItemType` propriedade o **ListView** controlar, a expressão de associação de dados `Item` está disponível e o controle se torna fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-143">By setting the `ItemType` property in the **ListView** control, the data-binding expression `Item` is available and the control becomes strongly typed.</span></span> <span data-ttu-id="0e1b9-144">Conforme mencionado no tutorial anterior, você pode selecionar os detalhes do objeto de Item usando o IntelliSense, como especificar o `ProductName`:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-144">As mentioned in the previous tutorial, you can select details of the Item object using IntelliSense, such as specifying the `ProductName`:</span></span>

![Exibir dados de itens e detalhes - IntelliSense](display_data_items_and_details/_static/image1.png)

<span data-ttu-id="0e1b9-146">Além disso, você estiver usando a associação de modelo para especificar um `SelectMethod` valor.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-146">In addition, you are using model binding to specify a `SelectMethod` value.</span></span> <span data-ttu-id="0e1b9-147">Esse valor (`GetProducts`) corresponderá ao método que você adicionará ao code-behind para exibir produtos na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-147">This value (`GetProducts`) will correspond to the method that you will add to the code behind to display products in the next step.</span></span>

### <a name="adding-code-to-display-products"></a><span data-ttu-id="0e1b9-148">Adicionando código para exibir produtos</span><span class="sxs-lookup"><span data-stu-id="0e1b9-148">Adding Code to Display Products</span></span>

<span data-ttu-id="0e1b9-149">Nesta etapa, você adicionará código para preencher o **ListView** controle com dados de produto do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-149">In this step, you'll add code to populate the **ListView** control with product data from the database.</span></span> <span data-ttu-id="0e1b9-150">O código dará suporte a produtos de exibição por categoria individual, bem como mostrando todos os produtos.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-150">The code will support showing products by individual category, as well as showing all products.</span></span>

1. <span data-ttu-id="0e1b9-151">Em **Solution Explorer**, clique com botão direito *ProductList. aspx* e, em seguida, clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-151">In **Solution Explorer**, right-click *ProductList.aspx* and then click **View Code**.</span></span>
2. <span data-ttu-id="0e1b9-152">Substitua o código existente no *ProductList.aspx.cs* arquivo com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-152">Replace the existing code in the *ProductList.aspx.cs* file with the following code:</span></span>   

    [!code-csharp[Main](display_data_items_and_details/samples/sample3.cs)]

<span data-ttu-id="0e1b9-153">Este código mostra o `GetProducts` método que é referenciado pelo `ItemType` propriedade do **ListView** controlar o *ProductList. aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-153">This code shows the `GetProducts` method that's referenced by the `ItemType` property of the **ListView** control in the *ProductList.aspx* page.</span></span> <span data-ttu-id="0e1b9-154">Para limitar os resultados a uma categoria específica no banco de dados, o código define o `categoryId` valor a partir do valor de cadeia de caracteres de consulta passado para o *ProductList. aspx* página quando o *ProductList. aspx* página é para onde navegar.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-154">To limit the results to a specific category in the database, the code sets the `categoryId` value from the query string value passed to the *ProductList.aspx* page when the *ProductList.aspx* page is navigated to.</span></span> <span data-ttu-id="0e1b9-155">O `QueryStringAttribute` classe no `System.Web.ModelBinding` namespace é usado para recuperar o valor da id de variável de cadeia de caracteres de consulta. Isso instrui a associação de modelo para tentar associar um valor de cadeia de caracteres de consulta para o `categoryId` parâmetro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-155">The `QueryStringAttribute` class in the `System.Web.ModelBinding` namespace is used to retrieve the value of the query string variable id. This instructs model binding to try to bind a value from the query string to the `categoryId` parameter at run time.</span></span>

<span data-ttu-id="0e1b9-156">Quando uma categoria válida é passada como uma cadeia de caracteres de consulta para a página, os resultados da consulta são limitados a esses produtos no banco de dados que correspondem a `categoryId` valor.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-156">When a valid category is passed as a query string to the page, the results of the query are limited to those products in the database that match the `categoryId` value.</span></span> <span data-ttu-id="0e1b9-157">Por exemplo, se a URL para o *ProductsList.aspx* página é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-157">For instance, if the URL to the *ProductsList.aspx* page is the following:</span></span>

[!code-console[Main](display_data_items_and_details/samples/sample4.cmd)]

<span data-ttu-id="0e1b9-158">A página exibe apenas os produtos onde o `category` é igual a `1`.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-158">The page displays only the products where the `category` equals `1`.</span></span>

<span data-ttu-id="0e1b9-159">Se nenhuma cadeia de caracteres de consulta está incluída ao navegar para o *ProductList. aspx* página, todos os produtos serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-159">If no query string is included when navigating to the *ProductList.aspx* page, all products will be displayed.</span></span>

<span data-ttu-id="0e1b9-160">As fontes de valores para esses métodos são chamadas de *valor provedores* (como *QueryString*), e os atributos de parâmetro que indicam qual provedor de valor para usar são chamados de valor atributos de provedor (como "`id`").</span><span class="sxs-lookup"><span data-stu-id="0e1b9-160">The sources of values for these methods are referred to as *value providers* (such as *QueryString*), and the parameter attributes that indicate which value provider to use are referred to as value provider attributes (such as "`id`").</span></span> <span data-ttu-id="0e1b9-161">O ASP.NET inclui provedores de valor e os atributos correspondentes para todas as fontes típicas de entrada do usuário em um aplicativo de Web Forms, como a cadeia de caracteres de consulta, cookies, valores de formulário, controles, estado de exibição, estado de sessão e propriedades de perfil.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-161">ASP.NET includes value providers and corresponding attributes for all of the typical sources of user input in a Web Forms application, such as the query string, cookies, form values, controls, view state, session state, and profile properties.</span></span> <span data-ttu-id="0e1b9-162">Você também pode escrever provedores de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-162">You can also write custom value providers.</span></span>

### <a name="running-the-application"></a><span data-ttu-id="0e1b9-163">Executando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0e1b9-163">Running the Application</span></span>

<span data-ttu-id="0e1b9-164">Execute o aplicativo agora para ver como você pode exibir todos os produtos ou apenas um conjunto de produtos limitado por categoria.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-164">Run the application now to see how you can view all of the products or just a set of products limited by category.</span></span>

1. <span data-ttu-id="0e1b9-165">No **Solution Explorer**, com o botão direito do *Default.aspx* página e selecione **exibir no navegador**.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-165">In the **Solution Explorer**, right-click the *Default.aspx* page and select **View in Browser**.</span></span>  
 <span data-ttu-id="0e1b9-166">O navegador será aberto e mostre o *Default.aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-166">The browser will open and show the *Default.aspx* page.</span></span>
2. <span data-ttu-id="0e1b9-167">Selecione **carros** no menu de navegação da categoria de produto.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-167">Select **Cars** from the product category navigation menu.</span></span>  
 <span data-ttu-id="0e1b9-168">O *ProductList. aspx* página é exibida, mostrando apenas os produtos incluídos na categoria "Carro".</span><span class="sxs-lookup"><span data-stu-id="0e1b9-168">The *ProductList.aspx* page is displayed showing only products included in the "Cars" category.</span></span> <span data-ttu-id="0e1b9-169">Posteriormente neste tutorial, você exibirá detalhes do produto.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-169">Later in this tutorial, you will display product details.</span></span>  

    ![Exibir dados de itens e detalhes - carros](display_data_items_and_details/_static/image2.png)
3. <span data-ttu-id="0e1b9-171">Selecione **produtos** no menu de navegação na parte superior.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-171">Select **Products** from the navigation menu at the top.</span></span>  
 <span data-ttu-id="0e1b9-172">Novamente, o *ProductList. aspx* página é exibida, mas desta vez, ele mostra a lista completa de produtos.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-172">Again, the *ProductList.aspx* page is displayed, however this time it shows the entire list of products.</span></span>   

    ![Exibir dados de itens e detalhes - produtos](display_data_items_and_details/_static/image3.png)
4. <span data-ttu-id="0e1b9-174">Feche o navegador e retorne ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-174">Close the browser and return to Visual Studio.</span></span>

### <a name="adding-a-data-control-to-display-product-details"></a><span data-ttu-id="0e1b9-175">Adicionando um controle de dados para exibir detalhes do produto</span><span class="sxs-lookup"><span data-stu-id="0e1b9-175">Adding a Data Control to Display Product Details</span></span>

<span data-ttu-id="0e1b9-176">Em seguida, você modificará a marcação no *ProductDetails.aspx* página que você adicionou no tutorial anterior, para que a página pode exibir informações sobre um produto individual.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-176">Next, you'll modify the markup in the *ProductDetails.aspx* page that you added in the previous tutorial so that the page can display information about an individual product.</span></span>

1. <span data-ttu-id="0e1b9-177">Em **Solution Explorer**, abra o *ProductDetails.aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-177">In **Solution Explorer**, open the *ProductDetails.aspx* page.</span></span>
2. <span data-ttu-id="0e1b9-178">Substitua a marcação existente com a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-178">Replace the existing markup with the following markup:</span></span>   

    [!code-aspx[Main](display_data_items_and_details/samples/sample5.aspx)]

<span data-ttu-id="0e1b9-179">Esse código usa um **FormView** controle para exibir detalhes sobre um produto individual.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-179">This code uses a **FormView** control to display details about an individual product.</span></span> <span data-ttu-id="0e1b9-180">Essa marcação usa métodos, como aqueles que são usados para exibir dados de *ProductList. aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-180">This markup uses methods like those that are used to display data in the *ProductList.aspx* page.</span></span> <span data-ttu-id="0e1b9-181">O **FormView** controle é usado para exibir um único registro em vez de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-181">The **FormView** control is used to display a single record at a time from a data source.</span></span> <span data-ttu-id="0e1b9-182">Quando você usa o **FormView** controle, você cria modelos para exibir e editar valores de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-182">When you use the **FormView** control, you create templates to display and edit data-bound values.</span></span> <span data-ttu-id="0e1b9-183">Os modelos contém controles, expressões de associação e a formatação que definem a aparência e a funcionalidade do formulário.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-183">The templates contain controls, binding expressions, and formatting that define the look and functionality of the form.</span></span>

<span data-ttu-id="0e1b9-184">Para conectar-se a marcação acima para o banco de dados, você deve adicionar o código adicional para o *ProductDetails.aspx* código.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-184">To connect the above markup to the database, you must add additional code to the *ProductDetails.aspx* code.</span></span>

1. <span data-ttu-id="0e1b9-185">Em **Solution Explorer**, clique com botão direito *ProductDetails.aspx* e, em seguida, clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-185">In **Solution Explorer**, right-click *ProductDetails.aspx* and then click **View Code**.</span></span>  
 <span data-ttu-id="0e1b9-186">O *ProductDetails.aspx.cs* arquivo será exibido.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-186">The *ProductDetails.aspx.cs* file will be displayed.</span></span>
2. <span data-ttu-id="0e1b9-187">Substitua o código existente pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0e1b9-187">Replace the existing code with the following code:</span></span>   

    [!code-csharp[Main](display_data_items_and_details/samples/sample6.cs)]

<span data-ttu-id="0e1b9-188">Esse código verifica um "`productID`" valor de cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-188">This code checks for a "`productID`" query-string value.</span></span> <span data-ttu-id="0e1b9-189">Se um valor de cadeia de consulta válido for encontrado, o produto será exibido.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-189">If a valid query-string value is found, the matching product is displayed.</span></span> <span data-ttu-id="0e1b9-190">Se nenhuma cadeia de consulta é encontrada, ou o valor de cadeia de caracteres de consulta não é válido, nenhum produto é exibido no *ProductDetails.aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-190">If no query-string is found, or the query-string value is not valid, no product is displayed on the *ProductDetails.aspx* page.</span></span>

### <a name="running-the-application"></a><span data-ttu-id="0e1b9-191">Executando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0e1b9-191">Running the Application</span></span>

<span data-ttu-id="0e1b9-192">Agora você pode executar o aplicativo para ver um produto individual exibido com base na id do produto.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-192">Now you can run the application to see an individual product displayed based on the id of the product.</span></span>

1. <span data-ttu-id="0e1b9-193">Pressione **F5** enquanto estiver no Visual Studio para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-193">Press **F5** while in Visual Studio to run the application.</span></span>  
 <span data-ttu-id="0e1b9-194">O navegador será aberto e mostre o *Default.aspx* página.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-194">The browser will open and show the *Default.aspx* page.</span></span>
2. <span data-ttu-id="0e1b9-195">Selecione "Barcos" no menu de navegação de categoria.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-195">Select "Boats" from the category navigation menu.</span></span>  
 <span data-ttu-id="0e1b9-196">O *ProductList. aspx* página é exibida.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-196">The *ProductList.aspx* page is displayed.</span></span>
3. <span data-ttu-id="0e1b9-197">Selecione o produto de "Documento barco" na lista de produtos.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-197">Select the "Paper Boat" product from the product list.</span></span>  
 <span data-ttu-id="0e1b9-198">O *ProductDetails.aspx* página é exibida.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-198">The *ProductDetails.aspx* page is displayed.</span></span>   

    ![Exibir dados de itens e detalhes - produtos](display_data_items_and_details/_static/image4.png)
4. <span data-ttu-id="0e1b9-200">Feche o navegador.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-200">Close the browser.</span></span>

## <a name="summary"></a><span data-ttu-id="0e1b9-201">Resumo</span><span class="sxs-lookup"><span data-stu-id="0e1b9-201">Summary</span></span>

<span data-ttu-id="0e1b9-202">Neste tutorial da série de você ter adicionar marcação e código para exibir uma lista de produtos e exibir detalhes do produto.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-202">In this tutorial of the series you have add markup and code to display a product list and to display product details.</span></span> <span data-ttu-id="0e1b9-203">Durante esse processo, você aprendeu sobre controles de dados fortemente tipados, associação de modelo e provedores de valor.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-203">During this process you have learned about strongly typed data controls, model binding, and value providers.</span></span> <span data-ttu-id="0e1b9-204">O seguinte tutorial, você adicionará um carrinho de compras para o aplicativo de exemplo Wingtip Toys.</span><span class="sxs-lookup"><span data-stu-id="0e1b9-204">In the next tutorial, you'll add a shopping cart to the Wingtip Toys sample application.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0e1b9-205">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0e1b9-205">Additional Resources</span></span>

[<span data-ttu-id="0e1b9-206">Recuperando e exibindo dados com o modelo de associação e formulários da web</span><span class="sxs-lookup"><span data-stu-id="0e1b9-206">Retrieving and displaying data with model binding and web forms</span></span>](../../presenting-and-managing-data/model-binding/retrieving-data.md)

>[!div class="step-by-step"]
<span data-ttu-id="0e1b9-207">[Anterior](ui_and_navigation.md)
[Próximo](shopping-cart.md)</span><span class="sxs-lookup"><span data-stu-id="0e1b9-207">[Previous](ui_and_navigation.md)
[Next](shopping-cart.md)</span></span>