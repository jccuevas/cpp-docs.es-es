---
title: _variant_t (Clase)
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: e11d31904fd8e54049f69ee4f6530d511c8c7f4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187757"
---
# <a name="_variant_t-class"></a>_variant_t (Clase)

**Específicos de Microsoft**

Un objeto **_variant_t** encapsula el tipo de datos `VARIANT`. La clase administra la asignación y desasignación de recursos, y realiza llamadas a funciones para `VariantInit` y `VariantClear` según corresponda.

### <a name="construction"></a>Construcción

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Construye un objeto de **_variant_t** .|

### <a name="operations"></a>Operaciones

|||
|-|-|
|[Adjuntar](../cpp/variant-t-attach.md)|Adjunta un objeto `VARIANT` al objeto **_variant_t** .|
|[Borrar](../cpp/variant-t-clear.md)|Borra el objeto de `VARIANT` encapsulado.|
|[ChangeType](../cpp/variant-t-changetype.md)|Cambia el tipo del objeto **_variant_t** a la `VARTYPE`indicada.|
|[Separar](../cpp/variant-t-detach.md)|Desasocia el objeto `VARIANT` encapsulado de este objeto **_variant_t** .|
|[SetString](../cpp/variant-t-setstring.md)|Asigna una cadena a este objeto **_variant_t** .|

### <a name="operators"></a>Operadores

|||
|-|-|
|[Operador =](../cpp/variant-t-operator-equal.md)|Asigna un nuevo valor a un objeto de **_variant_t** existente.|
|[operador = =,! =](../cpp/variant-t-relational-operators.md)|Compara dos objetos **_variant_t** para buscar igualdad o desigualdad.|
|[Extractores](../cpp/variant-t-extractors.md)|Extrae datos del objeto `VARIANT` encapsulado.|

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comutil. h >

**Lib:** omsuppw. lib o comsuppwd. lib (vea [/Zc: Wchar_t (Wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)

## <a name="see-also"></a>Consulte también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)
