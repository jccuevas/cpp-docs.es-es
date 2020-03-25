---
title: _com_ptr_t (Clase)
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: eeaab22ded537cbbb211a79596b8383251af3ab7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189914"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t (Clase)

**Específicos de Microsoft**

Un objeto **_com_ptr_t** encapsula un puntero de interfaz com y se denomina puntero "inteligente". Esta clase de plantilla administra la asignación y desasignación de recursos a través de llamadas de función a las funciones miembro de `IUnknown`: `QueryInterface`, `AddRef`y `Release`.

La definición typedef proporcionada por la macro _COM_SMARTPTR_TYPEDEF normalmente hace referencia a un puntero inteligente. Esta macro toma un nombre de interfaz y el IID y declara una especialización de **_com_ptr_t** con el nombre de la interfaz más un sufijo de `Ptr`. Por ejemplo:

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

declara el `IMyInterfacePtr`de especialización **_com_ptr_t** .

Un conjunto de [plantillas de función](../cpp/relational-function-templates.md), no miembros de esta clase de plantilla, admite comparaciones con un puntero inteligente en el lado derecho del operador de comparación.

### <a name="construction"></a>Construcción

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Construye un objeto de **_com_ptr_t** .|

### <a name="low-level-operations"></a>Operaciones de bajo nivel

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|Llama a la función miembro `AddRef` de `IUnknown` en el puntero de interfaz encapsulado.|
|[Adjuntar](../cpp/com-ptr-t-attach.md)|Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Crea una nueva instancia de un objeto a partir de un `CLSID` o `ProgID`.|
|[Separar](../cpp/com-ptr-t-detach.md)|Extrae y devuelve el puntero de interfaz encapsulado.|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Se adjunta a una instancia existente de un objeto, dado un `CLSID` o `ProgID`.|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Devuelve el puntero de interfaz encapsulado.|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Llama a la función miembro `QueryInterface` de `IUnknown` en el puntero de interfaz encapsulado.|
|[Versión](../cpp/com-ptr-t-release.md)|Llama a la función miembro `Release` de `IUnknown` en el puntero de interfaz encapsulado.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](../cpp/com-ptr-t-operator-equal.md)|Asigna un nuevo valor a un objeto de **_com_ptr_t** existente.|
|[operadores = =,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Compara el objeto de puntero inteligente con otro puntero inteligente, puntero de interfaz sin formato o NULL.|
|[Extractores](../cpp/com-ptr-t-extractors.md)|Extrae el puntero de interfaz COM encapsulado.|

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comip. h >

**Lib:** omsuppw. lib o comsuppwd. lib (vea [/Zc: Wchar_t (Wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)

## <a name="see-also"></a>Consulte también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)
