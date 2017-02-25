---
title: "Colecciones y enumeradores de ATL | Microsoft Docs"
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
  - "interfaces de colección"
  - "colecciones, clases ATL"
  - "interfaces de enumerador"
  - "enumeradores, clases ATL"
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Colecciones y enumeradores de ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`collection` es un objeto COM que proporciona una interfaz que permite el acceso a un grupo de elementos de datos \(los datos sin formato u otros objetos\).  Una interfaz que sigue las normas para proporcionar acceso a un grupo de objetos se conoce como *interfaz de intercalación*.  
  
 Como mínimo, las interfaces de intercalación deben proporcionar una propiedad de **Cuenta** que devuelve el número de elementos de la colección, una propiedad de **Elemento** que devuelve un elemento de la colección basándose en un índice, y una propiedad de `_NewEnum` que devuelve un enumerador para la colección.  Opcionalmente, las interfaces de intercalación pueden proporcionar métodos de **Agregar** y de **Quitar** para permitir que eliminans los elementos son insertados en o de la colección, y un método de **Borrar** para quitar todos los elementos.  
  
 `enumerator` es un objeto COM que proporciona una interfaz para recorrer en iteración los elementos de una colección.  Las interfaces de enumeradores proporcionan acceso serie a los elementos de una colección mediante cuatro métodos necesarios: `Next`, **Omitir**, **Restablecer**, y `Clone`.  
  
 Puede obtener más información sobre interfaces de enumerador leyendo sobre la interfaz arquetipo \(pero completamente imaginaria\) de.  
  
## En esta sección  
 [Clases de colección y de enumerador ATL](../atl/atl-collection-and-enumerator-classes.md)  
 Describe y proporciona brevemente vínculos a clases ATL que le ayudarán colecciones y enumeradores de implementan.  
  
 [Diseño Principles para las interfaces de colección y de enumerador](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 Describe los diversos principios de diseño subyacente de cada tipo de interfaz.  
  
 [implementar una colección STL\-Basada](../atl/implementing-an-stl-based-collection.md)  
 Un ejemplo ampliado que le guía por la implementación de una plantilla estándar \(STL\) Biblioteca\-basó la colección.  
  
## Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas conceptuales sobre cómo programar utilizando Active Template Library.  
  
 [Ejemplo ATLCollections](../top/visual-cpp-samples.md)  
 Un ejemplo que muestra el uso de `ICollectionOnSTLImpl` y de `CComEnumOnSTL`, y la implementación de clases de directivas de copia personalizadas.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)