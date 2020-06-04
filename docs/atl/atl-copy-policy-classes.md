---
title: Clases de política de copia de ATL
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: f40f31124d4547076249a7459ac4b63cc25305d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317389"
---
# <a name="atl-copy-policy-classes"></a>Clases de política de copia de ATL

Las clases de directiva de copia son [clases](../atl/utility-classes.md) de utilidad que se utilizan para inicializar, copiar y eliminar datos. Las clases de directiva de copia permiten definir la semántica de copia para cualquier tipo de datos y definir conversiones entre diferentes tipos de datos.

ATL utiliza clases de política de copia en sus implementaciones de las siguientes plantillas:

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

Al encapsular la información necesaria para copiar o convertir datos en una clase de directiva de copia que se puede pasar como argumento de plantilla, los desarrolladores de ATL han proporcionado una reutilización extrema de estas clases. Por ejemplo, si necesita implementar una colección con cualquier tipo de datos arbitrario, todo lo que necesita proporcionar es la directiva de copia adecuada; nunca tiene que tocar el código que implementa la colección.

## <a name="definition"></a>Definición

Por definición, una clase que proporciona las siguientes funciones estáticas es una clase de política de copia:

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

Puede reemplazar los `DestinationType` tipos y *SourceType* por tipos de datos arbitrarios para cada directiva de copia.

> [!NOTE]
> Aunque puede definir clases de directiva de copia para cualquier tipo de datos arbitrarios, el uso de las clases en código ATL debe limitar los tipos que tienen sentido. Por ejemplo, cuando se usa una clase de política de `DestinationType` copia con la colección o las implementaciones de enumerador de ATL, debe ser un tipo que se pueda usar como parámetro en un método de interfaz COM.

Utilice **init** para inicializar datos, **copiar** los datos y **destruirlos** para liberarlos. El significado preciso de inicialización, copia y destrucción es el dominio de la clase de directiva de copia y variará en función de los tipos de datos implicados.

Hay dos requisitos sobre el uso y la implementación de una clase de política de copia:

- El primer parámetro que se va a **copiar** solo debe recibir un puntero a los datos que haya inicializado previamente mediante **init**.

- **destroy** solo debe recibir un puntero a los datos que haya inicializado previamente mediante **init** o copiado mediante **copia.**

## <a name="standard-implementations"></a>Implementaciones estándar

ATL proporciona dos clases de `_Copy` directiva `_CopyInterface` de copia en forma de las clases de plantilla y:

- La `_Copy` clase solo permite la copia homogénea (no la conversión `DestinationType` entre tipos de datos) ya que solo ofrece un único parámetro de plantilla para especificar ambos y *SourceType*. La implementación genérica de esta plantilla no `memcpy` contiene código de inicialización o destrucción y se usa para copiar los datos. ATL también proporciona `_Copy` especializaciones para los tipos de datos VARIANT, LPOLESTR, OLEVERB y CONNECTDATA.

- La `_CopyInterface` clase proporciona una implementación para copiar punteros de interfaz siguiendo las reglas COM estándar. Una vez más esta clase solo permite la copia homogénea, por lo que utiliza una asignación simple y una llamada para `AddRef` realizar la copia.

## <a name="custom-implementations"></a>Implementaciones personalizadas

Normalmente, deberá definir sus propias clases de directiva de copia para la copia heterogénea (es decir, la conversión entre tipos de datos). Para ver algunos ejemplos de clases de directiva de copia personalizadas, consulte los archivos VCUE_Copy.h y VCUE_CopyString.h en el ejemplo [ATLCollections.](../overview/visual-cpp-samples.md) Estos archivos contienen dos `GenericCopy` clases de directiva de copia de plantilla y `MapCopy`, además de una serie de especializaciones de diferentes tipos de `GenericCopy` datos.

### <a name="genericcopy"></a>GenericCopy

`GenericCopy`le permite especificar *SourceType* y `DestinationType` como argumentos de plantilla. Esta es la forma más `GenericCopy` general de la clase de VCUE_Copy.h:

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h también contiene las siguientes especializaciones `GenericCopy<VARIANT, BSTR>` `GenericCopy<BSTR, VARIANT>`de esta clase: `GenericCopy<BSTR>`, , . VCUE_CopyString.h contiene especializaciones para copiar desde **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, y `GenericCopy<BSTR, std::string>`. Usted podría `GenericCopy` mejorar proporcionando más especializaciones de su propia.

### <a name="mapcopy"></a>MapCopy

`MapCopy`se supone que los datos que se copian se almacenan en un mapa de estilo de biblioteca estándar de C++, por lo que le permite especificar el tipo de mapa en el que se almacenan los datos y el tipo de destino. La implementación de la clase solo usa las typedefs proporcionadas por la clase `GenericCopy` *MapType* para determinar el tipo de los datos de origen y llamar a la clase adecuada. No se necesitan especializaciones de esta clase.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>Consulte también

[Implementación de una colección basada en biblioteca estándar C++](../atl/implementing-an-stl-based-collection.md)<br/>
[Ejemplo de ATLCollections](../overview/visual-cpp-samples.md)
