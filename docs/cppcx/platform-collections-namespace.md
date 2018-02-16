---
title: 'Platform:: Collections Namespace | Documentos de Microsoft'
ms.custom: 
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
dev_langs:
- C++
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4f7c99f99e0935fd96aa02240de2c0c72ce890a0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollections-namespace"></a>Platform::Collections (Espacio de nombres)

Contiene el espacio de nombres Platform:: Collections el `Map`, `MapView`, `Vector`, y `VectorView` clases. Estas clases son implementaciones concretas de las interfaces correspondientes que se definen en el espacio de nombres [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) . Los tipos de colección concretos no son portátiles a través de la ABI (por ejemplo, cuando un programa de JavaScript o de C# llama a un componente de C++), pero se pueden convertir implícitamente a sus tipos de interfaz correspondientes. Por ejemplo, si implementa un método público que rellena y devuelve una colección, use [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) para implementar la colección internamente y usa [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) como tipo de valor devuelto. Para obtener más información, consulte [colecciones](../cppcx/collections-c-cx.md) y [crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Puedes crear un objeto Platform::Collections::Vector a partir de un objeto [std::vector](../standard-library/vector-class.md) y un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) a partir de un objeto [std::map](../standard-library/map-class.md).

Además, el espacio de nombres Platform:: Collections proporciona compatibilidad para la nueva inserción e iteradores de entrada, y `Vector` y `VectorView` iteradores.

Debe incluir (`#include`) el encabezado collection.h para utilizar los tipos en el espacio de nombres Platform:: Collections.

## <a name="syntax"></a>Sintaxis

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Miembros

Este espacio de nombres contiene los miembros siguientes.

|nombre|Descripción|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator (Clase)](../cppcx/platform-collections-backinsertiterator-class.md)|Representa un iterador que inserta un elemento al final de una colección.|
|[Platform::Collections::InputIterator (Clase)](../cppcx/platform-collections-inputiterator-class.md)|Representa un iterador que inserta un elemento al principio de una colección.|
|[clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md)|Representa una colección modificable de pares clave-valor a los que se tiene acceso mediante una clave. Similar a [std::map](../standard-library/map-class.md).|
|[clase Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md)|Representa una colección de solo lectura de pares clave-valor a los que se tiene acceso mediante una clave.|
|[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)|Representa una secuencia modificable de elementos. Similar a [std::vector](../standard-library/vector-class.md).|
|[Platform::Collections::VectorIterator (Clase)](../cppcx/platform-collections-vectoriterator-class.md)|Representa un iterador que recorre una colección de `Vector` .|
|[clase Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)|Representa una secuencia de solo lectura de elementos.|
|[Platform::Collections::VectorViewIterator (Clase)](../cppcx/platform-collections-vectorviewiterator-class.md)|Representa un iterador que recorre una colección de `VectorView` .|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Requisitos

**Metadatos:** platform.winmd

**Espacio de nombres:** Platform::Collections

**Opción del compilador:** /ZW

## <a name="see-also"></a>Vea también

[Namespace de plataforma](../cppcx/platform-namespace-c-cx.md)  
