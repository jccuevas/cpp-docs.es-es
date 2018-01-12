---
title: Colecciones y enumeradores ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52b74f51733947ca46c0ddb1039f92ce7f69e670
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-collections-and-enumerators"></a>Colecciones y enumeradores de ATL
A `collection` es un objeto COM que proporciona una interfaz que permite el acceso a un grupo de elementos de datos (datos sin formato u otros objetos). Una interfaz que sigue las normas para proporcionar acceso a un grupo de objetos se conoce como un *interfaz de colección*.  
  
 Como mínimo, deben proporcionar interfaces de colección una **recuento** propiedad que devuelve el número de elementos de la colección, una **elemento** propiedad que devuelve un elemento de la colección basándose en un índice y un `_NewEnum` propiedad que devuelve un enumerador para la colección. Si lo desea, pueden proporcionar las interfaces de colección **agregar** y **quitar** métodos para permitir que los elementos se inserta o se elimina de la colección y un **desactive** método para quitar todos los elementos.  
  
 Un `enumerator` es un objeto COM que proporciona una interfaz para recorrer en iteración los elementos de una colección. Interfaces de enumerador proporcionan acceso de serie a los elementos de una colección a través de cuatro métodos requeridos: `Next`, **omitir**, **restablecer**, y `Clone`.  
  
 Se puede obtener más información sobre las interfaces de enumerador leyendo sobre arquetípico (pero completamente imaginaria) [interfaz IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx) interfaz.  
  
## <a name="in-this-section"></a>En esta sección  
 [Recopilación de ATL y clases de enumerador](../atl/atl-collection-and-enumerator-classes.md)  
 Describe brevemente y proporciona vínculos a las clases ATL que le ayudarán a implementan colecciones y enumeradores.  
  
 [Principios de diseño para la recopilación e interfaces de enumerador](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 Describe los principios de diseño diferentes detrás de cada tipo de interfaz.  
  
 [Implementar una recopilación basada en la biblioteca estándar de C++](../atl/implementing-an-stl-based-collection.md)  
 Un ejemplo extendido que le guía a través de la implementación de una colección basada en la biblioteca estándar de C++.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.  
  
 [Ejemplo ATLCollections](../visual-cpp-samples.md)  
 Un ejemplo que muestra el uso de `ICollectionOnSTLImpl` y `CComEnumOnSTL`y la implementación de clases de directivas de copia personalizadas.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)

