---
title: Colecciones y enumeradores ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00265d3ce0f8ea867021500777d93991d245be47
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204818"
---
# <a name="atl-collections-and-enumerators"></a>Colecciones y enumeradores de ATL
Un `collection` es un objeto COM que proporciona una interfaz que permite el acceso a un grupo de elementos de datos (datos sin formato u otros objetos). Una interfaz que sigue los estándares para proporcionar acceso a un grupo de objetos se conoce como un *interfaz de colección*.  
  
 Como mínimo, deben proporcionar interfaces de colección un `Count` propiedad que devuelve el número de elementos de la colección, un `Item` propiedad que devuelve un elemento de la colección basándose en un índice, y un `_NewEnum` propiedad que devuelve un enumerador para la colección. Si lo desea, pueden proporcionar interfaces de colección `Add` y `Remove` métodos para permitir que los elementos se insertan o eliminan de la colección y un `Clear` método para quitar todos los elementos.  
  
 Un `enumerator` es un objeto COM que proporciona una interfaz para recorrer en iteración los elementos de una colección. Interfaces de enumerador proporcionan acceso de serie a los elementos de una colección a través de cuatro métodos requeridos: `Next`, `Skip`, `Reset`, y `Clone`.  
  
 Puede aprender más sobre las interfaces de enumerador mediante la lectura de contenido de referencia como [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) interfaz.  
  
## <a name="in-this-section"></a>En esta sección  
 [Recopilación de ATL y clases de enumerador](../atl/atl-collection-and-enumerator-classes.md)  
 Describe brevemente y proporciona vínculos a las clases ATL que le ayudarán a implementan colecciones y enumeradores.  
  
 [Principios de diseño para la recopilación e interfaces de enumerador](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 Describe los principios de diseño diferentes detrás de cada tipo de interfaz.  
  
 [Implementar una recopilación basada en la biblioteca estándar de C++](../atl/implementing-an-stl-based-collection.md)  
 Un ejemplo completo que le guiará a través de la implementación de una colección basada en la biblioteca estándar de C++.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.  
  
 [Ejemplo ATLCollections](../visual-cpp-samples.md)  
 Un ejemplo que muestra el uso de `ICollectionOnSTLImpl` y `CComEnumOnSTL`y la implementación de clases de directivas de copia personalizadas.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)

