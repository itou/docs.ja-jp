---
title: SYSLIB0002 エラー
description: コンパイル時のエラー SYSLIB0002 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 00fd42975c9286221b75c87caef8d2109b9b7100
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333143"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a><span data-ttu-id="b98ce-103">SYSLIB0002: PrincipalPermissionAttribute は旧型式</span><span class="sxs-lookup"><span data-stu-id="b98ce-103">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>

<span data-ttu-id="b98ce-104"><xref:System.Security.Permissions.PrincipalPermissionAttribute> コンストラクターは旧型式であり、.NET 5.0 以降、コンパイル時のエラー `SYSLIB0002` を発生させます。</span><span class="sxs-lookup"><span data-stu-id="b98ce-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces compile-time error `SYSLIB0002`, starting in .NET 5.0.</span></span> <span data-ttu-id="b98ce-105">この属性をインスタンス化したり、メソッドに適用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b98ce-105">You cannot instantiate this attribute or apply it to a method.</span></span>

<span data-ttu-id="b98ce-106">他の非推奨警告とは異なり、エラーを非表示にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b98ce-106">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="b98ce-107">回避策</span><span class="sxs-lookup"><span data-stu-id="b98ce-107">Workarounds</span></span>

- <span data-ttu-id="b98ce-108">ASP.NET MVC アクション メソッドにこの属性を適用する場合:</span><span class="sxs-lookup"><span data-stu-id="b98ce-108">If you're applying the attribute to an ASP.NET MVC action method:</span></span>

  <span data-ttu-id="b98ce-109">ASP.NET に組み込まれている承認インフラストラクチャを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b98ce-109">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="b98ce-110">次のコードからは、<xref:System.Web.Mvc.AuthorizeAttribute> 属性を使用してコントローラーに注釈を付ける方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="b98ce-110">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="b98ce-111">ASP.NET ランタイムによって、アクションの実行前に、ユーザーが承認されます。</span><span class="sxs-lookup"><span data-stu-id="b98ce-111">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="b98ce-112">詳細については、「[ASP.NET Core でのロールベースの承認](/aspnet/core/security/authorization/roles)」と「[ASP.NET Core での承認の概要](/aspnet/core/security/authorization/introduction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b98ce-112">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="b98ce-113">Web アプリのコンテキスト外でライブラリ コードにこの属性を適用する場合:</span><span class="sxs-lookup"><span data-stu-id="b98ce-113">If you're applying the attribute to library code outside the context of a web app:</span></span>

  <span data-ttu-id="b98ce-114"><xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> メソッドを呼び出して、メソッドの先頭で手動によるチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="b98ce-114">Perform the checks manually at the beginning of your method by calling the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

## <a name="see-also"></a><span data-ttu-id="b98ce-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b98ce-115">See also</span></span>

- [<span data-ttu-id="b98ce-116">PrincipalPermissionAttribute は現在使用されていないエラーです</span><span class="sxs-lookup"><span data-stu-id="b98ce-116">PrincipalPermissionAttribute is obsolete as error</span></span>](3.1-5.0.md#principalpermissionattribute-is-obsolete-as-error)