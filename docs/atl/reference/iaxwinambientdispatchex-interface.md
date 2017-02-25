---
title: "IAxWinAmbientDispatchEx Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IAxWinAmbientDispatchEx"
  - "IAxWinAmbientDispatchEx"
  - "ATL::IAxWinAmbientDispatchEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinAmbientDispatchEx interface"
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# IAxWinAmbientDispatchEx Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta interfaz implementa las propiedades de ambiente complementarios para un control hospedado.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      MIDL_INTERFACE( "B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5" )  
IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[SetAmbientDispatch](../Topic/IAxWinAmbientDispatchEx::SetAmbientDispatch.md)|Se llama a este método para complementar la interfaz ambiente predeterminada de propiedad con una interfaz definida por el usuario.|  
  
## Comentarios  
 Incluya esta interfaz en aplicaciones vinculadas estáticamente a ATL y hospedan Controles ActiveX, especialmente los Controles ATL ActiveX que tienen propiedades de Ambient.  No incluyendo esta interfaz generará esta aserción: “¿Ha olvidado pasar el LIBID a CComModule::Init?”  
  
 Esta interfaz es expuesta por el control ActiveX ATL que hospeda objetos.  Derivado de [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` agrega un método que permite complemente la interfaz ambiente de la propiedad proporcionada por ATL con uno propio.  
  
 [AXHost](https://msdn.microsoft.com/en-us/library/system.windows.forms.axhost.aspx) intentará cargar la información de tipo sobre `IAxWinAmbientDispatch` y `IAxWinAmbientDispatchEx` de la biblioteca de tipos que contiene el código.  
  
 Si está vinculando a ATL90.dll, **AXHost** cargará la información de tipos de la biblioteca de tipos en una DLL.  
  
 Vea [Hospedar Controles ActiveX mediante ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para más detalles.  
  
## Requisitos  
 La definición de esta interfaz está disponible con varios formatos, como se muestra en la tabla siguiente.  
  
|Tipo de definición|Archivo|  
|------------------------|-------------|  
|IDL|atliface.idl|  
|Biblioteca de tipos|ATL.dll|  
|C\+\+|atliface.h \(también incluido en ATLBase.h\)|  
  
## Vea también  
 [IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)