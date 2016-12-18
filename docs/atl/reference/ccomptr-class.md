---
title: "CComPtr Class | Microsoft Docs"
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
  - "CComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComPtr class"
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase de puntero inteligente para administrar punteros de interfaz COM.  
  
## Sintaxis  
  
```  
  
      template<  
   class T   
>  
class CComPtr  
```  
  
#### Parámetros  
 `T`  
 Una interfaz COM que especifica el tipo de puntero que se va a almacenar.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)|el constructor.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPtr::operator \=](../Topic/CComPtr::operator%20=.md)|Asigna un puntero al puntero de miembro.|  
  
## Comentarios  
 ATL utiliza `CComPtr` y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) para administrar punteros de interfaz COM.  Ambos se derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md), y realizan el recuento de referencias automático.  
  
 Las clases de **CComPtr** y de [CComQIPtr](../../atl/reference/ccomqiptr-class.md) pueden ayudar a eliminar pérdidas de memoria realizando el recuento de referencias automático.  Las siguientes funciones ambas realizan las mismas operaciones lógicas; sin embargo, observe que la segunda versión puede ser menos propenso a errores mediante la clase de **CComPtr** :  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/CPP/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/CPP/ccomptr-class_2.cpp)]  
  
 En compilaciones de depuración, vínculo atlsd.lib para el seguimiento codificada.  
  
## Jerarquía de herencia  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)   
 [CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)   
 [Class Overview](../../atl/atl-class-overview.md)