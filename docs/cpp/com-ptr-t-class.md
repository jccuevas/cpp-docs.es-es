---
title: _com_ptr_t (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t
dev_langs:
- C++
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02e3c0833423f2e9eb8eebfe2c15a46466ef3c58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073578"
---
# <a name="comptrt-class"></a>_com_ptr_t (Clase)

**Específicos de Microsoft**

Un **_com_ptr_t** objeto encapsula un puntero de interfaz COM y se llama a un puntero "inteligente". Esta clase de plantilla administra la asignación de recursos y la desasignación con llamadas de función para la `IUnknown` funciones miembro: `QueryInterface`, `AddRef`, y `Release`.

Normalmente, la definición typedef proporcionada por la macro _COM_SMARTPTR_TYPEDEF hace referencia a un puntero inteligente. Esta macro toma un nombre de interfaz y el IID y declara una especialización de **_com_ptr_t** con el nombre de la interfaz más un sufijo de `Ptr`. Por ejemplo:

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

declara el **_com_ptr_t** especialización `IMyInterfacePtr`.

Un conjunto de [plantillas de función](../cpp/relational-function-templates.md), no los miembros de esta plantilla de clase, admite las comparaciones con un puntero inteligente en el lado derecho del operador de comparación.

### <a name="construction"></a>Construcción

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Construye un **_com_ptr_t** objeto.|

### <a name="low-level-operations"></a>Operaciones de bajo nivel

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|Las llamadas del `AddRef` función miembro de `IUnknown` en el puntero de interfaz encapsulado.|
|[Asociar](../cpp/com-ptr-t-attach.md)|Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Crea una nueva instancia de un objeto, dado un `CLSID` o `ProgID`.|
|[Desasociar](../cpp/com-ptr-t-detach.md)|Extrae y devuelve el puntero de interfaz encapsulado.|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Se asocia a una instancia existente de un objeto dada una `CLSID` o `ProgID`.|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Devuelve el puntero de interfaz encapsulado.|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Las llamadas del `QueryInterface` función miembro de `IUnknown` en el puntero de interfaz encapsulado.|
|[Release](../cpp/com-ptr-t-release.md)|Las llamadas del `Release` función miembro de `IUnknown` en el puntero de interfaz encapsulado.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](../cpp/com-ptr-t-operator-equal.md)|Asigna un nuevo valor a una existente **_com_ptr_t** objeto.|
|[los operadores ==,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Comparar el objeto de puntero inteligente a otro puntero inteligente, puntero de interfaz sin formato, o NULL.|
|[Extractores de datos](../cpp/com-ptr-t-extractors.md)|Extrae el puntero de interfaz COM encapsulado.|

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comip.h >

**Lib:** omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)

## <a name="see-also"></a>Vea también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)