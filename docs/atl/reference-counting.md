---
title: "Reference Counting | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef method [C++]"
  - "AddRef method [C++], reference counting"
  - "reference counting"
  - "reference counts"
  - "referencias, contar"
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Reference Counting
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM propio automáticamente no intenta quitar un objeto de memoria si piensa que el objeto ya no se utiliza.  En su lugar, el programador del objeto debe quitar el objeto no.  El programador determina si un objeto se puede quitar basándose en un recuento de referencia.  
  
 COM usan métodos de **IUnknown** , [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [Liberar](http://msdn.microsoft.com/library/windows/desktop/ms682317), administrar el recuento de referencias de interfaces en un objeto.  Las reglas generales para llamar a estos métodos son:  
  
-   Cuando un cliente recibe un puntero de interfaz, `AddRef` se debe llamar a la interfaz.  
  
-   Siempre que el cliente ha terminado de utilizar el puntero de interfaz, debe llamar a **Liberar**.  
  
 En una implementación simple, incrementos de cada llamada de `AddRef` y disminuye de cada llamada de **Liberar** una variable de contador dentro del objeto.  Cuando las actualizaciones a cero de recuento, la interfaz dejan de cualquier usuario y están libres de quitarse de memoria.  
  
 El recuento de referencias también puede implementarse para contar cada referencia al objeto \(no una interfaz individual\).  En este caso, los delegados cada `AddRef` y llamada de **Liberar** a una implementación central en el objeto, y **Liberar** libera el objeto completo cuando su recuento de referencias llega a cero.  
  
> [!NOTE]
>  Cuando `CComObject`\- el objeto derivado se construyen mediante el operador de **nuevo** , el recuento de referencias es 0.  Por consiguiente, una llamada a `AddRef` debe ser realizada después correctamente de crear `CComObject`\- objeto derivado.  
  
## Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Managing Object Lifetimes through Reference Counting](http://msdn.microsoft.com/library/windows/desktop/ms687260)