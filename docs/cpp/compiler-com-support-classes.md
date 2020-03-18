---
title: Clases de compatibilidad con COM del compilador
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 1a9ff7c57965c9ba00881d5fe48501a6138b31d1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444423"
---
# <a name="compiler-com-support-classes"></a>Clases de compatibilidad con COM del compilador

**Específicos de Microsoft**

Las clases estándar se utilizan para proporcionar compatibilidad con algunos de los tipos COM. Las clases se definen en \<comdef. h > y los archivos de encabezado generados a partir de la biblioteca de tipos.

|Clase|Propósito|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Encapsula el tipo `BSTR` para proporcionar operadores y métodos útiles.|
|[_com_error](../cpp/com-error-class.md)|Define el objeto de error producido por [_com_raise_error](../cpp/com-raise-error.md) en la mayoría de los errores.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Encapsula los punteros de interfaz COM y automatiza las llamadas necesarias a `AddRef`, `Release`y `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Encapsula el tipo `VARIANT` para proporcionar operadores y métodos útiles.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)<br/>
[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)