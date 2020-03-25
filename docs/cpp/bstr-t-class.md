---
title: _bstr_t (Clase)
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: 3ef89c6f6742d528c427c49fd2a62d8820625e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190383"
---
# <a name="_bstr_t-class"></a>_bstr_t (Clase)

**Específicos de Microsoft**

Un objeto `_bstr_t` encapsula el [tipo de datos BSTR](/previous-versions/windows/desktop/automat/bstr). La clase administra la asignación y desasignación de recursos a través de las llamadas de función a `SysAllocString` y `SysFreeString` y otras API de `BSTR` cuando sea necesario. La clase **_bstr_t** usa el recuento de referencias para evitar una sobrecarga excesiva.

### <a name="construction"></a>Construcción

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Construye un objeto `_bstr_t`.|

### <a name="operations"></a>Operaciones

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|Copia un valor `BSTR` en el valor `BSTR` contenido en `_bstr_t`.|
|[Adjuntar](../cpp/bstr-t-attach.md)|Vincula un contenedor `_bstr_t` a un `BSTR`.|
|[copy](../cpp/bstr-t-copy.md)|Crea una copia del objeto `BSTR` encapsulado.|
|[Separar](../cpp/bstr-t-detach.md)|Devuelve el `BSTR` contenido en `_bstr_t` y desasocia `BSTR` de `_bstr_t`.|
|[GetAddress](../cpp/bstr-t-getaddress.md)|Apunta al `BSTR` contenido en `_bstr_t`.|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Señala al principio del objeto `BSTR` incluido en `_bstr_t`.|
|[length](../cpp/bstr-t-length.md)|Devuelve el número de caracteres de `_bstr_t`.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](../cpp/bstr-t-operator-equal.md)|Asigna un nuevo valor a un objeto `_bstr_t` existente.|
|[operador + =](../cpp/bstr-t-operator-add-equal-plus.md)|Agrega caracteres al final del objeto `_bstr_t`.|
|[operador +](../cpp/bstr-t-operator-add-equal-plus.md)|Concatena dos cadenas.|
|[operador !](../cpp/bstr-t-operator-logical-not.md)|Comprueba si el `BSTR` encapsulado es una cadena nula.|
|[operador = =,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Compara dos objetos `_bstr_t`.|
|[Operator wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrae los punteros al objeto `BSTR` multibyte o Unicode encapsulado.|

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comutil. h >

**Lib:** omsuppw. lib o comsuppwd. lib (vea [/Zc: Wchar_t (Wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)

## <a name="see-also"></a>Consulte también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)
