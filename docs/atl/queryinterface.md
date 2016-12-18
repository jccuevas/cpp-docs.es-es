---
title: "QueryInterface | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces, disponibilidad"
  - "interfaces, punteros"
  - "QueryInterface (método)"
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# QueryInterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque hay los mecanismos por los que un objeto puede expresar la funcionalidad que proporcione estáticamente \(antes de que se crea instancias\), el mecanismo COM fundamental es utilizar el método de **IUnknown** denominado [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Cada interfaz se deriva de **IUnknown**, por lo que cada interfaz tiene una implementación de `QueryInterface`.  Independientemente de la implementación, este método consulta un objeto mediante el IID de la interfaz en la que el llamador desea un puntero.  Si la de comunicación, `QueryInterface` de objeto recuperan un puntero a la interfaz, mientras que también llama a `AddRef`.  De lo contrario, devuelve el código de error **E\_NOINTERFACE** .  
  
 Observe que debe seguir las reglas de [recuento de referencias](../atl/reference-counting.md) siempre.  Si llama a **Liberar** en un puntero de interfaz para disminuir el recuento de referencias en cero, no debe utilizar ese puntero de nuevo.  Puede ser necesario ocasionalmente obtener una referencia parcial a un objeto \(es decir, quizás desee obtener un puntero a una de las interfaces sin aumentar el recuento de referencias\), pero no es aceptable hacerlo llamando a `QueryInterface` seguido de **Liberar**.  El puntero obtenido de esta forma no es válida y no se debe utilizar.  Este se vuelve más fácilmente manifiesto cuando se define [\_ATL\_DEBUG\_INTERFACES](../Topic/_ATL_DEBUG_INTERFACES.md) , por lo que la definición de esta macro es una forma útil de errores del recuento de referencias de buscar.  
  
## Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [QueryInterface: Navigating in an Object](http://msdn.microsoft.com/library/windows/desktop/ms687230)