---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: b6f1cc45f9666fc0fbd2332ac7bb7e539ec77cd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223654"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Define varios tipos y funciones que controlan la asignación y liberación de almacenamiento bajo el control del programa. También define los componentes para la creación de informes de errores de administración de almacenamiento.

## <a name="syntax"></a>Sintaxis

```cpp
#include <new>
```

## <a name="remarks"></a>Comentarios

Algunas de las funciones declaradas en este encabezado son reemplazables. La implementación proporciona una versión predeterminada, cuyo comportamiento se describe en este documento. No obstante, un programa puede definir una función con la misma firma para reemplazar la versión predeterminada en tiempo de vinculación. La versión de reemplazo debe cumplir los requisitos descritos en este documento.

### <a name="objects"></a>de la empresa

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Proporciona un objeto que se usará como un argumento para el **nothrow** versiones de **nueva** y **eliminar**.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Tipo que apunta a una función que se puede usar como un nuevo controlador.|

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Instala una función de usuario que se llama cuando el nuevo controlador no puede asignar memoria.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator delete](../standard-library/new-operators.md#op_delete)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para objetos individuales.|
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para una matriz de objetos.|
|[operator new](../standard-library/new-operators.md#op_new)|Función a la que llama una expresión new para asignar el almacenamiento para objetos individuales.|
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Función a la que llama una expresión new para asignar el almacenamiento para una matriz de objetos.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[bad_alloc (Clase)](../standard-library/bad-alloc-class.md)|Clase que describe una excepción que se produce para indicar que una solicitud de asignación no se realizó correctamente.|
|[nothrow_t Class](../standard-library/nothrow-t-structure.md)|Clase que se usa como parámetro de función del operador new para indicar que la función debe devolver un puntero nulo para notificar un error de asignación, en lugar de producir una excepción.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
