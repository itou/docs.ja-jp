---
description: '詳細情報: <udpTransportSettings>'
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: bfd862009401fef160939fb9acaa66fc9ca23ddb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749156"
---
# \<udpTransportSettings>

この構成要素は、の UDP トランスポート設定を公開 [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md) します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpDiscoveryEndpoint>**](udpdiscoveryendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|重複するメッセージを特定するためにトランスポートによって使用されるメッセージ ハッシュの最大数を指定する整数。  重複の検出は、TransportManager レベルで実行されます。 このプロパティを 0 に設定すると、重複の検出は無効になります。<br /><br /> この属性を使用して、システムの管理者や開発者は重複するメッセージの検出アルゴリズムをオフにできます。 これは、独自の重複検出アルゴリズムを実行する場合に望ましいことがあります。<br /><br /> 既定値は 4112 です。|  
|maxBufferPoolSize|トランスポートによって使用されるバッファー プールの最大サイズを指定する整数。|  
|maxMulticastRetransmitCount|メッセージを (最初に送信した後に) 再送信する最大回数を指定する整数。<br /><br /> 既定値は 2 です。|  
|maxPendingMessageCount|受信して、各チャネル インスタンスの InputQueue からまだ削除していないメッセージの最大数を指定する整数。  InputQueue が保留メッセージ数の上限に達すると、メッセージは削除されます。<br /><br /> 既定値は 32 です。|  
|maxReceivedMessageSize|バインディングで処理できるメッセージの最大サイズを指定する整数。<br /><br /> 既定値は 65507 です。|  
|maxUnicastRetransmitCount|メッセージを (最初に送信した後に) 再送信する最大回数を指定する整数。  メッセージをユニキャスト アドレスに送信し、対応する RelatesTo ヘッダーの付いた応答メッセージを受信すると、再送信は早期に (再送信の回数が構成された回数に到達する前に) 終了することがあります。<br /><br /> 既定値は 1 です。|  
|multicastInterfaceId|マルチホーム コンピューター上でマルチキャスト トラフィックを送受信するときに使用するネットワーク アダプターを一意に識別する文字列。 実行時には、トランスポートは、この属性値を使用してインターフェイスのインデックスを参照します。このインデックスは、その後、`IP_MULTICAST_IF` および `IPV6_MULTICAST_IF` のソケット オプションの設定に使用されます。  マルチキャスト グループに参加するときには、同じインターフェイス インデックスが使用されます (該当する場合)。<br /><br /> 既定値は `null` です。|  
|socketReceiveBufferSize|基になる WinSock ソケットの受信バッファー サイズを指定する整数。<br /><br /> 受信チャネルのユーザーは、バインディング上のこの属性を使用して、データ受信時のシステム動作を制御できます。  たとえば、受信 WCF メッセージを最大しきい値で利用するアプリケーションがある場合、この属性値よりも大きい値を使用すると、アプリケーションが処理できるようになるまで待機している間、メッセージを WinSock バッファーにスタックできます。  同じ状況で低い値を使用すると、メッセージが破棄される原因となる場合があります。 この属性は、基になる WinSock ソケットオプションを公開し `SO_RCVBUF` ます。この属性値は、以上のサイズである必要があり `maxReceivedMessageSize` ます。   これをより小さい値に設定する `maxReceivedMessageSize` と、ランタイム例外が発生します。<br /><br /> 既定値は 65536 です。|  
|timeToLive|マルチキャスト パケットが走査できるネットワーク セグメント ホップの数を指定する整数。  この属性は、`IP_MULTICAST_TTL` および `IP_TTL` ソケット オプションに関連付けられている機能を公開します。<br /><br /> 既定値は 1 です。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|固定探索コントラクトと UDP トランスポート バインディングを持つ標準エンドポイント。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
