---
title: "_U_STRINGorID Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL._U_STRINGorID"
  - "ATL::_U_STRINGorID"
  - "_U_STRINGorID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_STRINGorID class"
  - "U_STRINGorID class"
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# _U_STRINGorID Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase de adaptador de argumento permite nombres de recursos \(s de`LPCTSTR`\) o los id. de recurso \(s de**UINT**\) que se pasarán a una función sin requerir que el llamador convertir el identificador a una cadena mediante la macro de **MAKEINTRESOURCE** .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class _U_STRINGorID  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[\_U\_STRINGorID::\_U\_STRINGorID](../Topic/_U_STRINGorID::_U_STRINGorID.md)|el constructor.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[\_U\_STRINGorID::m\_lpstr](../Topic/_U_STRINGorID::m_lpstr.md)|El identificador de recursos.|  
  
## Comentarios  
 Esta clase está diseñada para implementar contenedores a la administración de recursos API de Windows como las funciones de [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042), de [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), y de [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) , que aceptan un argumento de `LPCTSTR` que puede ser el nombre de un recurso o su identificador  
  
 La clase define dos sobrecargas del constructor: uno acepta un argumento de `LPCTSTR` y el otro acepta un argumento de **UINT** .  El argumento de **UINT** se convierte en un compatible del tipo de recurso con funciones de administración de recursos de Windows mediante la macro de **MAKEINTRESOURCE** y el resultado almacenados en el único miembro de datos de la clase, [m\_lpstr](../Topic/_U_STRINGorID::m_lpstr.md).  El argumento al constructor de `LPCTSTR` se almacena directamente sin conversión.  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)