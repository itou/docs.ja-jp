---
title: SYSLIB0002 エラー
description: コンパイル時のエラー SYSLIB0002 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 774675e96d11a8e1b5d82767695d0defd1e8cfad
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596312"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a>SYSLIB0002: PrincipalPermissionAttribute は旧型式

<xref:System.Security.Permissions.PrincipalPermissionAttribute> コンストラクターは旧型式であり、.NET 5.0 以降、コンパイル時のエラー `SYSLIB0002` を発生させます。 この属性をインスタンス化したり、メソッドに適用したりすることはできません。

他の非推奨警告とは異なり、エラーを非表示にすることはできません。

## <a name="workarounds"></a>回避策

- ASP.NET MVC アクション メソッドにこの属性を適用する場合:

  ASP.NET に組み込まれている承認インフラストラクチャを使用することを検討してください。 次のコードからは、<xref:System.Web.Mvc.AuthorizeAttribute> 属性を使用してコントローラーに注釈を付ける方法がわかります。 ASP.NET ランタイムによって、アクションの実行前に、ユーザーが承認されます。

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

  詳細については、「[ASP.NET Core でのロールベースの承認](/aspnet/core/security/authorization/roles)」と「[ASP.NET Core での承認の概要](/aspnet/core/security/authorization/introduction)」を参照してください。

- Web アプリのコンテキスト外でライブラリ コードにこの属性を適用する場合:

  <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> メソッドを呼び出して、メソッドの先頭で手動によるチェックを実行します。

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

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>関連項目

- [PrincipalPermissionAttribute は現在使用されていないエラーです](../core-libraries/5.0/principalpermissionattribute-obsolete.md)
