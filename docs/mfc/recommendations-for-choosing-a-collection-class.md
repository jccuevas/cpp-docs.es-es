---
title: "Recomendaciones para elegir una clase de colección | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 312e777d86d2fd24ae84fe05b4162e1470f77e3b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Recommendations for Choosing a Collection (Clase)
Este artículo contiene información detallada diseñada para ayudarle a elegir una clase de colección para sus necesidades concretas de aplicación.  
  
 La elección de una clase de colección depende de varios factores, incluidos:  
  
-   Las características de la forma de clase: orden, indexación y rendimiento, como se muestra en la tabla siguiente [Características de la forma de colección](#_core_collection_shape_features) de este tema.  
  
-   Si la clase usa plantillas de C++  
  
-   Si los elementos almacenados en la colección pueden serializarse  
  
-   Si los elementos almacenados en la colección pueden volcarse para diagnósticos  
  
-   Si la colección tiene seguridad de tipos  
  
 En la siguiente tabla, [Características de la forma de colección](#_core_collection_shape_features), se resumen las características de las formas de colección disponibles.  
  
-   Las columnas 2 y 3 describen las características de acceso y ordenación de cada forma. En la tabla, el término "ordenado" significa que el orden en el que se insertan o eliminan los elementos determina su orden en la colección; no significa que los elementos se ordenan por su contenido. El término “indexado” significa que los elementos de la colección se pueden recuperar mediante un índice entero, como los elementos de una matriz estándar.  
  
-   Las columnas 4 y 5 describen el rendimiento de cada forma. En aplicaciones que requieren muchas inserciones en la colección, la velocidad de inserción puede ser especialmente importante; para otras aplicaciones, puede ser más importante la velocidad de búsqueda.  
  
-   En la columna 6 se describe si cada forma permite elementos duplicados.  
  
### <a name="_core_collection_shape_features"></a>  Características de la forma de colección  
  
|Forma|Por orden |Indizar|Insertar un elemento|Buscar un elemento especificado|Los elementos duplicados|  
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|  
|Lista|Sí|No|Rápido|Lento|Sí|  
|Matriz|Sí|Por entero|Lento|Lento|Sí|  
|Asignación|No|Por clave|Rápido|Rápido|No (claves) Sí (valores)|  
  
 En la siguiente tabla, [Características de clases de colección de MFC](#_core_characteristics_of_mfc_collection_classes), se resumen otras características importantes de las clases de colección específicas de MFC como guía para su selección. Su elección puede depender de si la clase se basa en plantillas de C++, de si sus elementos se pueden serializar a través del mecanismo de [serialización](../mfc/serialization-in-mfc.md) de documentos de MFC, de si sus elementos se pueden volcar mediante el mecanismo de volcado para diagnóstico de MFC o de si la clase tiene seguridad de tipos, es decir, si puede garantizar el tipo de elementos almacenados y recuperados de una colección basada en la clase.  
  
### <a name="_core_characteristics_of_mfc_collection_classes"></a>  Características de clases de colección de MFC  
  
|Clase|Usa C++<br /><br /> plantillas|Puede ser<br /><br /> serialized|Puede ser<br /><br /> volcado|Es<br /><br /> con seguridad de tipos|  
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|  
|`CArray`|Sí|Sí 1|Sí 1|No|  
|`CByteArray`|No|Sí|Sí|Sí 3|  
|`CDWordArray`|No|Sí|Sí|Sí 3|  
|`CList`|Sí|Sí 1|Sí 1|No|  
|`CMap`|Sí|Sí 1|Sí 1|No|  
|`CMapPtrToPtr`|No|No|Sí|No|  
|`CMapPtrToWord`|No|No|Sí|No|  
|`CMapStringToOb`|No|Sí|Sí|No|  
|`CMapStringToPtr`|No|No|Sí|No|  
|`CMapStringToString`|No|Sí|Sí|Sí 3|  
|`CMapWordToOb`|No|Sí|Sí|No|  
|`CMapWordToPtr`|No|No|Sí|No|  
|`CObArray`|No|Sí|Sí|No|  
|`CObList`|No|Sí|Sí|No|  
|`CPtrArray`|No|No|Sí|No|  
|`CPtrList`|No|No|Sí|No|  
|`CStringArray`|No|Sí|Sí|Sí 3|  
|`CStringList`|No|Sí|Sí|Sí 3|  
|`CTypedPtrArray`|Sí|Depende 2|Sí|Sí|  
|`CTypedPtrList`|Sí|Depende 2|Sí|Sí|  
|`CTypedPtrMap`|Sí|Depende 2|Sí|Sí|  
|`CUIntArray`|No|No|Sí|Sí 3|  
|`CWordArray`|No|Sí|Sí|Sí 3|  
  
 1. Para serializar, debe llamar explícitamente el objeto de colección `Serialize` función; para volcar, debe llamar explícitamente su `Dump` función. No puede usar el formato `ar << collObj` para serializar ni el formato `dmp` `<< collObj` para volcar.  
  
 2. La posibilidad de serializar depende del tipo de colección subyacente. Por ejemplo, si una matriz de puntero con tipo se basa en `CObArray`, es serializable; si se basa en `CPtrArray`, no es serializable. En general, las clases "Ptr" no se pueden serializar.  
  
 3. Si marca Sí en esta columna, una clase de colección no basada en plantillas tiene seguridad de tipos, siempre que la use según lo previsto. Por ejemplo, si almacena bytes en una `CByteArray`, la matriz tiene seguridad de tipos. Pero si la usa para almacenar caracteres, su seguridad de tipos es más incierta.  
  
## <a name="see-also"></a>Vea también  
 [Colecciones](../mfc/collections.md)   
 [Clases basadas en plantillas](../mfc/template-based-classes.md)   
 [Cómo: crear una colección con seguridad de tipos](../mfc/how-to-make-a-type-safe-collection.md)   
 [Acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md)

