---
title: "CStrBufT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CStrBufT<TCharType>"
  - "ATL.CStrBufT"
  - "CStrBufT"
  - "ATL::CStrBufT"
  - "ATL.CStrBufT<TCharType>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStrBufT class"
  - "shared classes, CStrBufT"
  - "cadenas [C++], custom memory management"
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CStrBufT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona la limpieza automática de recursos para `GetBuffer` y las llamadas de `ReleaseBuffer` en un objeto existente de `CStringT` .  
  
## Sintaxis  
  
```  
  
      template<  
   typename TCharType  
>  
class CStrBufT  
```  
  
#### Parámetros  
 *TCharType*  
 El tipo de caracteres de la clase de `CStrBufT` .  Puede ser una de las siguientes:  
  
-   `char` \(para las cadenas de caracteres ANSI\)  
  
-   `wchar_t` \(para las cadenas de caracteres Unicode\)  
  
-   **TCHAR** \(para ANSI y las cadenas de caracteres Unicode\)  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`PCXSTR`|un puntero a una cadena constante.|  
|`PXSTR`|un puntero a una cadena.|  
|`StringType`|El tipo string cuyo búfer debe tratarse por especializaciones de esta plantilla de clase.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](../Topic/CStrBufT::CStrBufT.md)|El constructor del objeto de búfer de cadena.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStrBufT::SetLength](../Topic/CStrBufT::SetLength.md)|Establece la longitud del búfer del carácter del objeto string asociado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](../Topic/CStrBufT::operator%20PCXSTR.md)|Recupera un puntero de **const** al búfer del carácter del objeto string asociado.|  
|[CStrBufT::operator PXSTR](../Topic/CStrBufT::operator%20PXSTR.md)|Recupera un puntero al búfer del carácter del objeto string asociado.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStrBufT::AUTO\_LENGTH](../Topic/CStrBufT::AUTO_LENGTH.md)|Automáticamente determine la nueva longitud de cadena en el inicio.|  
|[CStrBufT::SET\_LENGTH](../Topic/CStrBufT::SET_LENGTH.md)|Establece la longitud del objeto string en tiempo de GetBuffer|  
  
## Comentarios  
 esta clase se utiliza como clase contenedora para reemplazar llamadas a [GetBuffer](../Topic/CSimpleStringT::GetBuffer.md) y [ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md), o [GetBufferSetLength](../Topic/CSimpleStringT::GetBufferSetLength.md) y `ReleaseBuffer`.  
  
 Diseñado principalmente como clase auxiliar, `CStrBufT` proporciona una manera cómoda para que un desarrollador ejecute el búfer del carácter de un objeto string sin preocuparse de cómo o de cuándo llamar a `ReleaseBuffer`.  Esto es posible porque el objeto contenedor sale del ámbito de forma natural en el caso de una excepción o rutas de acceso de código de varias que dejan; hacer que su destructor libere el recurso de cadena.  
  
## Requisitos  
 **encabezado:** atlsimpstr.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)