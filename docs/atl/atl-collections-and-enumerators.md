---
title: Colecciones y enumeradores de ATL
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 502bedb1773dc2a6edbd6679d50e9c5946228283
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491900"
---
# <a name="atl-collections-and-enumerators"></a>Colecciones y enumeradores de ATL

Un `collection` es un objeto com que proporciona una interfaz que permite el acceso a un grupo de elementos de datos (datos sin procesar u otros objetos). Una interfaz que sigue los estándares para proporcionar acceso a un grupo de objetos se conoce como *interfaz de colección*.

Como mínimo, las interfaces de colección deben proporcionar `Count` una propiedad que devuelva el número de elementos de la colección `Item` , una propiedad que devuelve un elemento de la colección basándose en un índice `_NewEnum` , y una propiedad que devuelve un enumerador de la colección. Opcionalmente, las interfaces de colección `Add` pueden `Remove` proporcionar métodos y para permitir que los elementos se inserten o se eliminen de `Clear` la colección, y un método para quitar todos los elementos.

Un `enumerator` es un objeto com que proporciona una interfaz para recorrer en iteración los elementos de una colección. Las interfaces de enumerador proporcionan acceso en serie a los elementos de una colección mediante `Next`cuatro `Skip`métodos necesarios: `Clone`,, `Reset`y.

Puede obtener más información sobre las interfaces de enumerador mediante la lectura de contenido de referencia como la interfaz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

## <a name="in-this-section"></a>En esta sección

[Recopilación de ATL y clases de enumerador](../atl/atl-collection-and-enumerator-classes.md)<br/>
Describe brevemente y proporciona vínculos a las clases ATL que le ayudarán a implementar colecciones y enumeradores.

[Principios de diseño para la recopilación e interfaces de enumerador](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
Describe los diferentes principios de diseño que hay detrás de cada tipo de interfaz.

[Implementar una recopilación basada en la biblioteca estándar de C++](../atl/implementing-an-stl-based-collection.md)<br/>
Un ejemplo extendido que le guía por la implementación de una C++ colección basada en biblioteca estándar.

## <a name="related-sections"></a>Secciones relacionadas

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.

[Ejemplo de ATLCollections](../overview/visual-cpp-samples.md)<br/>
Un ejemplo que muestra el uso de `ICollectionOnSTLImpl` y `CComEnumOnSTL`, y la implementación de clases de directivas de copia personalizadas.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)
