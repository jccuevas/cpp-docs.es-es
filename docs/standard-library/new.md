---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: 6155a89c9cbba67ce27253aa64ff70ca7871e748
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457690"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Define varios tipos y funciones que controlan la asignación y liberación de almacenamiento bajo el control del programa. También define los componentes para la creación de informes de errores de administración de almacenamiento.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<new>

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Algunas de las funciones declaradas en este encabezado son reemplazables. La implementación proporciona una versión predeterminada, cuyo comportamiento se describe en este documento. No obstante, un programa puede definir una función con la misma firma para reemplazar la versión predeterminada en tiempo de vinculación. La versión de reemplazo debe cumplir los requisitos descritos en este documento.

## <a name="members"></a>Miembros

### <a name="objects"></a>de la empresa

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Proporciona un objeto que se va a usar como argumento para  las versiones nothrow de **New** y **Delete**.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Tipo que apunta a una función que se puede usar como un nuevo controlador.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>Funciones

|||
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[blanqueo](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Instala una función de usuario que se llama cuando el nuevo controlador no puede asignar memoria.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator delete](../standard-library/new-operators.md#op_delete)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para objetos individuales.|
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para una matriz de objetos.|
|[operator new](../standard-library/new-operators.md#op_new)|Función a la que llama una expresión new para asignar el almacenamiento para objetos individuales.|
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Función a la que llama una expresión new para asignar el almacenamiento para una matriz de objetos.|

### <a name="enums"></a>Enumeraciones

|||
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Clases

|||
|-|-|
|[bad_alloc Class](../standard-library/bad-alloc-class.md)|Clase que describe una excepción que se produce para indicar que una solicitud de asignación no se realizó correctamente.|
|[Clase bad_array_new_length](../standard-library/bad-array-new-length.md)||
|[nothrow_t Class](../standard-library/nothrow-t-structure.md)|Clase que se usa como parámetro de función del operador new para indicar que la función debe devolver un puntero nulo para notificar un error de asignación, en lugar de producir una excepción.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
