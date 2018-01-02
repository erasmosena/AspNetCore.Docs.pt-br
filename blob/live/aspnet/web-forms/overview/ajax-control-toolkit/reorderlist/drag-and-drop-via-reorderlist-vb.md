---
uid: web-forms/overview/ajax-control-toolkit/reorderlist/drag-and-drop-via-reorderlist-vb
title: Arrastar e soltar via ReorderList (VB) | Microsoft Docs
author: wenz
description: /Data-Access/Tutorials/Master-Detail-Using-a-bulleted-List-of-Master-Records-with-a-Details-DataList-VB
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: 848e6bcf-4c3f-4d14-974d-e45b9444ab79
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/reorderlist/drag-and-drop-via-reorderlist-vb
msc.type: authoredcontent
ms.openlocfilehash: e193a31fc86b7e8733d0b2fba371d99c62783d6c
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2017
---
<a name="drag-and-drop-via-reorderlist-vb"></a><span data-ttu-id="935fd-103">Arrastar e soltar via ReorderList (VB)</span><span class="sxs-lookup"><span data-stu-id="935fd-103">Drag and Drop via ReorderList (VB)</span></span>
====================
<span data-ttu-id="935fd-104">por [Christian Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="935fd-104">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="935fd-105">[Baixar o código](http://download.microsoft.com/download/9/3/f/93f8daea-bebd-4821-833b-95205389c7d0/ReorderList5.vb.zip) ou [baixar PDF](http://download.microsoft.com/download/2/d/c/2dc10e34-6983-41d4-9c08-f78f5387d32b/reorderlist5VB.pdf)</span><span class="sxs-lookup"><span data-stu-id="935fd-105">[Download Code](http://download.microsoft.com/download/9/3/f/93f8daea-bebd-4821-833b-95205389c7d0/ReorderList5.vb.zip) or [Download PDF](http://download.microsoft.com/download/2/d/c/2dc10e34-6983-41d4-9c08-f78f5387d32b/reorderlist5VB.pdf)</span></span>

> <span data-ttu-id="935fd-106">O controle ReorderList no AJAX Control Toolkit fornece uma lista que pode ser reordenada por usuário por meio de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="935fd-106">The ReorderList control in the AJAX Control Toolkit provides a list that can be reordered by the user via drag and drop.</span></span> <span data-ttu-id="935fd-107">A ordem atual da lista deverá ser persistida no servidor.</span><span class="sxs-lookup"><span data-stu-id="935fd-107">The current order of the list shall be persisted on the server.</span></span>


## <a name="overview"></a><span data-ttu-id="935fd-108">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="935fd-108">Overview</span></span>

<span data-ttu-id="935fd-109">O `ReorderList` controle no AJAX Control Toolkit fornece uma lista que pode ser reordenada por usuário por meio de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="935fd-109">The `ReorderList` control in the AJAX Control Toolkit provides a list that can be reordered by the user via drag and drop.</span></span> <span data-ttu-id="935fd-110">A ordem atual da lista deverá ser persistida no servidor.</span><span class="sxs-lookup"><span data-stu-id="935fd-110">The current order of the list shall be persisted on the server.</span></span>

## <a name="steps"></a><span data-ttu-id="935fd-111">Etapas</span><span class="sxs-lookup"><span data-stu-id="935fd-111">Steps</span></span>

<span data-ttu-id="935fd-112">O `ReorderList` controle oferece suporte a dados de associação de um banco de dados à lista.</span><span class="sxs-lookup"><span data-stu-id="935fd-112">The `ReorderList` control supports binding data from a database to the list.</span></span> <span data-ttu-id="935fd-113">O melhor de tudo, ele também suporta gravando alterações ordem do elemento de lista para o repositório de dados.</span><span class="sxs-lookup"><span data-stu-id="935fd-113">Best of all, it also supports writing changes to the order of the list element back to the data store.</span></span>

<span data-ttu-id="935fd-114">Este exemplo usa o Microsoft SQL Server 2005 Express Edition como armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="935fd-114">This sample uses Microsoft SQL Server 2005 Express Edition as the data store.</span></span> <span data-ttu-id="935fd-115">O banco de dados é uma parte opcional (e livre) de uma instalação do Visual Studio, incluindo o express edition.</span><span class="sxs-lookup"><span data-stu-id="935fd-115">The database is an optional (and free) part of a Visual Studio installation, including express edition.</span></span> <span data-ttu-id="935fd-116">Ele também está disponível como um download separado em [https://go.microsoft.com/fwlink/?LinkId=64064](https://go.microsoft.com/fwlink/?LinkId=64064).</span><span class="sxs-lookup"><span data-stu-id="935fd-116">It is also available as a separate download under [https://go.microsoft.com/fwlink/?LinkId=64064](https://go.microsoft.com/fwlink/?LinkId=64064).</span></span> <span data-ttu-id="935fd-117">Para este exemplo, vamos supor que a instância do SQL Server 2005 Express Edition é chamada `SQLEXPRESS` e reside no mesmo computador que o servidor web; isso também é a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="935fd-117">For this sample, we assume that the instance of the SQL Server 2005 Express Edition is called `SQLEXPRESS` and resides on the same machine as the web server; this is also the default setup.</span></span> <span data-ttu-id="935fd-118">Se sua configuração for diferente, você precisa se adaptar as informações de conexão para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="935fd-118">If your setup differs, you have to adapt the connection information for the database.</span></span>

<span data-ttu-id="935fd-119">A maneira mais fácil de configurar o banco de dados é usar o Microsoft SQL Server Management Studio Express ([https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang = en](https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang=en) ).</span><span class="sxs-lookup"><span data-stu-id="935fd-119">The easiest way to set up the database is to use the Microsoft SQL Server Management Studio Express ([https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang=en](https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang=en) ).</span></span> <span data-ttu-id="935fd-120">Conectar-se ao servidor, clique duas vezes em `Databases` e criar um novo banco de dados (com o botão direito e escolha `New Database`) chamado `Tutorials`.</span><span class="sxs-lookup"><span data-stu-id="935fd-120">Connect to the server, double-click on `Databases` and create a new database (right-click and choose `New Database`) called `Tutorials`.</span></span>

<span data-ttu-id="935fd-121">Este banco de dados, criar uma nova tabela chamada `AJAX` com as seguintes quatro colunas:</span><span class="sxs-lookup"><span data-stu-id="935fd-121">In this database, create a new table called `AJAX` with the following four columns:</span></span>

- <span data-ttu-id="935fd-122">`id`(inteiro chave primário, identidade, não NULL)</span><span class="sxs-lookup"><span data-stu-id="935fd-122">`id` (primary key, integer, identity, not NULL)</span></span>
- <span data-ttu-id="935fd-123">`char`(char (1), NULL)</span><span class="sxs-lookup"><span data-stu-id="935fd-123">`char` (char(1), NULL)</span></span>
- <span data-ttu-id="935fd-124">`description`(varchar (50), NULL)</span><span class="sxs-lookup"><span data-stu-id="935fd-124">`description` (varchar(50), NULL)</span></span>
- <span data-ttu-id="935fd-125">`position`(int, NULL)</span><span class="sxs-lookup"><span data-stu-id="935fd-125">`position` (int, NULL)</span></span>


<span data-ttu-id="935fd-126">[![O layout da tabela AJAX](drag-and-drop-via-reorderlist-vb/_static/image2.png)](drag-and-drop-via-reorderlist-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="935fd-126">[![The layout of the AJAX table](drag-and-drop-via-reorderlist-vb/_static/image2.png)](drag-and-drop-via-reorderlist-vb/_static/image1.png)</span></span>

<span data-ttu-id="935fd-127">O layout da tabela AJAX ([clique para exibir a imagem em tamanho normal](drag-and-drop-via-reorderlist-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="935fd-127">The layout of the AJAX table ([Click to view full-size image](drag-and-drop-via-reorderlist-vb/_static/image3.png))</span></span>


<span data-ttu-id="935fd-128">Em seguida, preencha a tabela com um par de valores.</span><span class="sxs-lookup"><span data-stu-id="935fd-128">Next, fill the table with a couple of values.</span></span> <span data-ttu-id="935fd-129">Observe que o `position` coluna mantém a ordem de classificação dos elementos.</span><span class="sxs-lookup"><span data-stu-id="935fd-129">Note that the `position` column holds the sort order of the elements.</span></span>


<span data-ttu-id="935fd-130">[![Os dados iniciais na tabela AJAX](drag-and-drop-via-reorderlist-vb/_static/image5.png)](drag-and-drop-via-reorderlist-vb/_static/image4.png)</span><span class="sxs-lookup"><span data-stu-id="935fd-130">[![The initial data in the AJAX table](drag-and-drop-via-reorderlist-vb/_static/image5.png)](drag-and-drop-via-reorderlist-vb/_static/image4.png)</span></span>

<span data-ttu-id="935fd-131">Os dados iniciais na tabela de AJAX ([clique para exibir a imagem em tamanho normal](drag-and-drop-via-reorderlist-vb/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="935fd-131">The initial data in the AJAX table ([Click to view full-size image](drag-and-drop-via-reorderlist-vb/_static/image6.png))</span></span>


<span data-ttu-id="935fd-132">A próxima etapa requer para gerar um `SqlDataSource` controle para se comunicar com o novo banco de dados e sua tabela.</span><span class="sxs-lookup"><span data-stu-id="935fd-132">The next step requires to generate an `SqlDataSource` control to communicate with the new database and its table.</span></span> <span data-ttu-id="935fd-133">A fonte de dados deve oferecer suporte a `SELECT` e `UPDATE` comandos SQL.</span><span class="sxs-lookup"><span data-stu-id="935fd-133">The data source must support the `SELECT` and `UPDATE` SQL commands.</span></span> <span data-ttu-id="935fd-134">Quando a ordem dos elementos de lista for alterada posteriormente, o `ReorderList` controle envia automaticamente os dois valores para a fonte de dados `Update` comando: a nova posição e a ID do elemento.</span><span class="sxs-lookup"><span data-stu-id="935fd-134">When the order of the list elements is later changed, the `ReorderList` control automatically submits two values to the data source's `Update` command: the new position and the ID of the element.</span></span> <span data-ttu-id="935fd-135">Portanto, a fonte de dados necessidades um `<UpdateParameters>` seção para esses dois valores:</span><span class="sxs-lookup"><span data-stu-id="935fd-135">Therefore, the data source needs an `<UpdateParameters>` section for these two values:</span></span>

[!code-aspx[Main](drag-and-drop-via-reorderlist-vb/samples/sample1.aspx)]

<span data-ttu-id="935fd-136">O `ReorderList` controle precisa definir os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="935fd-136">The `ReorderList` control needs to set the following attributes:</span></span>

- <span data-ttu-id="935fd-137">`AllowReorder`: Se os itens da lista podem ser reorganizados</span><span class="sxs-lookup"><span data-stu-id="935fd-137">`AllowReorder`: Whether the list items may be rearranged</span></span>
- <span data-ttu-id="935fd-138">`DataSourceID`: A ID da fonte de dados</span><span class="sxs-lookup"><span data-stu-id="935fd-138">`DataSourceID`: The ID of the data source</span></span>
- <span data-ttu-id="935fd-139">`DataKeyField`: O nome da coluna de chave primária na fonte de dados</span><span class="sxs-lookup"><span data-stu-id="935fd-139">`DataKeyField`: The name of the primary key column in the data source</span></span>
- <span data-ttu-id="935fd-140">`SortOrderField`: A coluna de fonte de dados que fornece a ordem de classificação para os itens de lista</span><span class="sxs-lookup"><span data-stu-id="935fd-140">`SortOrderField`: The data source column that provides the sort order for the list items</span></span>

<span data-ttu-id="935fd-141">No `<DragHandleTemplate>` e `<ItemTemplate>` seções, o layout da lista pode ser ajustado.</span><span class="sxs-lookup"><span data-stu-id="935fd-141">In the `<DragHandleTemplate>` and `<ItemTemplate>` sections, the layout of the list can be fine-tuned.</span></span> <span data-ttu-id="935fd-142">Além disso, é possível vinculação de dados usando o `Eval()` método, como visto aqui:</span><span class="sxs-lookup"><span data-stu-id="935fd-142">Also, databinding is possible using the `Eval()` method, as seen here:</span></span>

[!code-aspx[Main](drag-and-drop-via-reorderlist-vb/samples/sample2.aspx)]

<span data-ttu-id="935fd-143">Informações de estilo CSS a seguir (referenciado no `<DragHandleTemplate>` seção o `ReorderList` controle) torna-se de que o ponteiro do mouse muda adequadamente quando ele passa sobre a alça de arraste:</span><span class="sxs-lookup"><span data-stu-id="935fd-143">The following CSS style information (referenced in the `<DragHandleTemplate>` section of the `ReorderList` control) makes sure that the mouse pointer changes appropriately when it hovers over the drag handle:</span></span>

[!code-css[Main](drag-and-drop-via-reorderlist-vb/samples/sample3.css)]

<span data-ttu-id="935fd-144">Por fim, um `ScriptManager` controle inicializa o ASP.NET AJAX para a página:</span><span class="sxs-lookup"><span data-stu-id="935fd-144">Finally, a `ScriptManager` control initializes ASP.NET AJAX for the page:</span></span>

[!code-aspx[Main](drag-and-drop-via-reorderlist-vb/samples/sample4.aspx)]

<span data-ttu-id="935fd-145">Executar este exemplo no navegador e reorganizar os itens da lista um pouco.</span><span class="sxs-lookup"><span data-stu-id="935fd-145">Run this example in the browser and rearrange the list items a bit.</span></span> <span data-ttu-id="935fd-146">Em seguida, recarregue a página e/ou examinar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="935fd-146">Then, reload the page and/or have a look at the database.</span></span> <span data-ttu-id="935fd-147">As posições alteradas ter sido mantidas e também são refletidas pelos valores de `position` coluna no banco de dados e que tudo sem qualquer código, apenas usando marcação.</span><span class="sxs-lookup"><span data-stu-id="935fd-147">The altered positions have been maintained and are also reflected by the values in the `position` column in the database and that all without any code, just by using markup.</span></span>


<span data-ttu-id="935fd-148">[![Os dados nas alterações do banco de dados de acordo com a nova ordem de item de lista](drag-and-drop-via-reorderlist-vb/_static/image8.png)](drag-and-drop-via-reorderlist-vb/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="935fd-148">[![The data in the database changes according to the new list item order](drag-and-drop-via-reorderlist-vb/_static/image8.png)](drag-and-drop-via-reorderlist-vb/_static/image7.png)</span></span>

<span data-ttu-id="935fd-149">Os dados nas alterações do banco de dados de acordo com a nova lista de ordem de item ([clique para exibir a imagem em tamanho normal](drag-and-drop-via-reorderlist-vb/_static/image9.png))</span><span class="sxs-lookup"><span data-stu-id="935fd-149">The data in the database changes according to the new list item order ([Click to view full-size image](drag-and-drop-via-reorderlist-vb/_static/image9.png))</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="935fd-150">Anterior</span><span class="sxs-lookup"><span data-stu-id="935fd-150">Previous</span></span>](using-postbacks-with-reorderlist-vb.md)