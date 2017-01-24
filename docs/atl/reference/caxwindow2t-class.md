---
title: "CAxWindow2T Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAxWindow2T<TBase>"
  - "ATL::CAxWindow2T"
  - "CAxWindow2T"
  - "ATL.CAxWindow2T<TBase>"
  - "ATL.CAxWindow2T"
  - "CAxWindow2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAxWindow2 class"
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAxWindow2T Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX, y también tienen compatibilidad para hospedar controles ActiveX con licencia.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <   
class TBase= CWindow   
>  
class CAxWindow2T :   
public CAxWindowT< TBase >  
```  
  
#### Parámetros  
 *TBase*  
 La clase de la que `CAxWindowT` deriva.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAxWindow2T::CAxWindow2T](../Topic/CAxWindow2T::CAxWindow2T.md)|Crea un objeto `CAxWindow2T`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAxWindow2T::Create](../Topic/CAxWindow2T::Create.md)|Crea una ventana host.|  
|[CAxWindow2T::CreateControlLic](../Topic/CAxWindow2T::CreateControlLic.md)|Crea un control ActiveX con licencia, se inicializa, y los hospedarlo en la ventana especificada.|  
|[CAxWindow2T::CreateControlLicEx](../Topic/CAxWindow2T::CreateControlLicEx.md)|Crea un control ActiveX con licencia, se inicializa, los hospedarlo en la ventana especificada, y recupera un puntero de interfaz \(o a punteros\) del control.|  
|[CAxWindow2T::GetWndClassName](../Topic/CAxWindow2T::GetWndClassName.md)|método estático que recupera el nombre de la clase de ventana.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAxWindow2T::operator \=](../Topic/CAxWindow2T::operator%20=.md)|asigna `HWND` a un objeto existente de `CAxWindow2T` .|  
  
## Comentarios  
 `CAxWindow2T` proporciona los métodos para manipular una ventana que hospeda un control ActiveX.  `CAxWindow2T` también admite para hospedar controles ActiveX con licencia.  El hospedaje proporcionado por “**AtlAxWinLic80**”, que es ajustará en `CAxWindow2T`.  
  
 La clase `CAxWindow2` se implementa como una especialización de la clase de `CAxWindow2T` .  se declara esta especialización como:  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
>  documentan los miembros de`CAxWindowT` en [CAxWindow](../../atl/reference/caxwindow-class.md).  
  
 Vea [Hospedar Controles ActiveX mediante ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que utiliza miembros de esta clase.  
  
## Jerarquía de herencia  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Preguntas más frecuentes sobre contención de controles](../../atl/atl-control-containment-faq.md)