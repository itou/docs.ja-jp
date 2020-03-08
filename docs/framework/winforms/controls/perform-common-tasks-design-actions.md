---
title: コントロールに対するデザイナーアクションを使用した一般的なタスクの実行
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634895"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a><span data-ttu-id="be396-102">チュートリアル: デザイナーアクションを使用した一般的なタスクの実行</span><span class="sxs-lookup"><span data-stu-id="be396-102">Walkthrough: Perform common tasks using designer actions</span></span>

<span data-ttu-id="be396-103">Windows フォームアプリケーションのフォームとコントロールを構築する際には、繰り返し実行する多くのタスクがあります。</span><span class="sxs-lookup"><span data-stu-id="be396-103">As you construct forms and controls for your Windows Forms application, there are many tasks you'll perform repeatedly.</span></span> <span data-ttu-id="be396-104">次の一覧は、一般的に実行されるタスクの一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="be396-104">The following list shows some of the commonly performed tasks you'll come across:</span></span>

- <span data-ttu-id="be396-105"><xref:System.Windows.Forms.TabControl>のタブを追加または削除する。</span><span class="sxs-lookup"><span data-stu-id="be396-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>
- <span data-ttu-id="be396-106">コントロールをその親にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="be396-106">Docking a control to its parent.</span></span>
- <span data-ttu-id="be396-107"><xref:System.Windows.Forms.SplitContainer> コントロールの向きを変更する。</span><span class="sxs-lookup"><span data-stu-id="be396-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="be396-108">開発を高速化するために、多くのコントロールはデザイナーアクションを提供しています。これは、デザイン時に1つのジェスチャでこのような一般的なタスクを実行できるようにする、状況依存のメニューです。</span><span class="sxs-lookup"><span data-stu-id="be396-108">To speed development, many controls offer designer actions, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="be396-109">これらのタスクは、*デザイナーアクション動詞*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="be396-109">These tasks are called *designer actions verbs*.</span></span>

<span data-ttu-id="be396-110">デザイナーのアクションは、デザイナーの有効期間にわたってコントロールインスタンスにアタッチされたままになり、常に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="be396-110">Designer actions remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="be396-111">プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="be396-111">Create the project</span></span>

<span data-ttu-id="be396-112">最初にプロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="be396-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="be396-113">Visual Studio で、 **DesignerActionsExample**という名前の Windows ベースのアプリケーションプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="be396-113">In Visual Studio, create a Windows-based application project called **DesignerActionsExample**.</span></span>

2. <span data-ttu-id="be396-114">**Windows フォームデザイナー**でフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="be396-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-designer-actions"></a><span data-ttu-id="be396-115">デザイナーアクションを使用する</span><span class="sxs-lookup"><span data-stu-id="be396-115">Use designer actions</span></span>

<span data-ttu-id="be396-116">デザイナーアクションは、デザイン時に、それらを提供するコントロールに対して常に使用できます。</span><span class="sxs-lookup"><span data-stu-id="be396-116">Designer actions are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="be396-117">**[ツールボックス]** から <xref:System.Windows.Forms.TabControl> をフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="be396-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="be396-118"><xref:System.Windows.Forms.TabControl>の横に表示されるデザイナーアクショングリフ (![小さい黒い矢印](./media/designer-actions-glyph.gif)) に注意してください。</span><span class="sxs-lookup"><span data-stu-id="be396-118">Note the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="be396-119">[デザイナーアクション] グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="be396-119">Click the designer actions glyph.</span></span> <span data-ttu-id="be396-120">グリフの横に表示されるショートカットメニューで、 **[タブの追加]** 項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="be396-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="be396-121">新しいタブページが <xref:System.Windows.Forms.TabControl>に追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="be396-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="be396-122"><xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="be396-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="be396-123">[デザイナーアクション] グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="be396-123">Click the designer actions glyph.</span></span> <span data-ttu-id="be396-124">グリフの横に表示されるショートカットメニューで、 **[列の追加]** 項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="be396-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="be396-125">新しい列が <xref:System.Windows.Forms.TableLayoutPanel> コントロールに追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="be396-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="be396-126"><xref:System.Windows.Forms.SplitContainer> ツールボックス **から** コントロールをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="be396-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="be396-127">[デザイナーアクション] グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="be396-127">Click the designer actions glyph.</span></span> <span data-ttu-id="be396-128">グリフの横に表示されるショートカットメニューで、 **[横スプリッターの方向]** 項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="be396-128">In the shortcut menu that appears next to the glyph, select the **Horizontal Splitter Orientation** item.</span></span> <span data-ttu-id="be396-129"><xref:System.Windows.Forms.SplitContainer> コントロールのスプリッターバーが水平方向に配置されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="be396-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="be396-130">参照</span><span class="sxs-lookup"><span data-stu-id="be396-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>