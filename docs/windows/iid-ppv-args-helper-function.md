---
title: "IID_PPV_ARGS_Helper (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/IID_PPV_ARGS_Helper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IID_PPV_ARGS_Helper (función)"
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IID_PPV_ARGS_Helper (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba que el tipo de argumento especificado se deriva de la interfaz de `IUnknown` .  
  
> [!IMPORTANT]
>  Esta una especialización de plantilla admite la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.  Utilice en su lugar [IID\_PPV\_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) .  
  
## Sintaxis  
  
```  
template<  
   typename T  
>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### Parámetros  
 `T`  
 El tipo de argumento `pp`.  
  
 `pp`  
 Un puntero doble\-indirecto.  
  
## Valor devuelto  
 El argumento `pp` convertido a un puntero\-a\-uno\- puntero a `void`.  
  
## Comentarios  
 Se genera un error en tiempo de compilación si el parámetro `T` de plantilla no deriva de `IUnknown`.  
  
## Requisitos  
 **Encabezado:** client.h  
  
## Vea también  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/es-es/00000000-0000-0000-0000-000000000000)