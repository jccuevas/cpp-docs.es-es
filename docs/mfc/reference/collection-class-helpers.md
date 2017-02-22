---
title: "Aplicaciones auxiliares de clase de colecci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de colección, funciones auxiliares"
  - "ConstructElements (función)"
  - "DestructElements (función)"
  - "clase de colección de funciones auxiliares"
  - "SerializeElements (función)"
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# Aplicaciones auxiliares de clase de colecci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases de colección `CMap`, `CList`, y aplicación auxiliar global con plantilla uso de `CArray` funcionan para propósitos tales como comparando, copiar, y serializando elementos.  Como parte de la implementación de clases basadas en `CMap`, `CList`, y `CArray`, debe invalidar estas funciones según sea necesario con versiones adecuadas al tipo de datos del mapa, lista, matriz o.  Para obtener información sobre reemplazar funciones auxiliares como `SerializeElements`, vea el artículo [Colecciones: Cómo crear una colección de tipo](../../mfc/how-to-make-a-type-safe-collection.md).  Observe que han quedado obsoletas **ConstructElements** y **DestructElements** .  
  
 La biblioteca Microsoft Foundation Class proporciona funciones globales siguientes para ayudarle a personalizar las clases de colección:  
  
### Aplicaciones auxiliares de la clase de colección  
  
|||  
|-|-|  
|[CompareElements](../Topic/CompareElements.md)|Indica si los elementos son iguales.|  
|[CopyElements](../Topic/CopyElements.md)|Copiar elementos de una matriz a otra.|  
|[DumpElements](../Topic/DumpElements.md)|Proporciona secuencia\- orientó salida de diagnóstico.|  
|[HashKey](../Topic/HashKey.md)|Calcula una clave hash.|  
|[SerializeElements](../Topic/SerializeElements.md)|Almacenar o recuperar elementos a o desde un archivo.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMap Class](../../mfc/reference/cmap-class.md)   
 [CList Class](../../mfc/reference/clist-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)