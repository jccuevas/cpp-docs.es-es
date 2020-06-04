---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: b9ddb3117afe37060b8013be235bdb11a2a031ac
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898850"
---
# <a name="ltsystem_errorgt"></a>&lt;system_error&gt;

Incluya el encabezado \<system_error > para definir la clase de excepción `system_error` y las plantillas relacionadas para procesar los errores del sistema de bajo nivel.

## <a name="requirements"></a>Requisitos de

**Encabezado:** \<system_error>

**Espacio de nombres:** std

## <a name="members"></a>Members

### <a name="objects"></a>Objetos

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Representa la categoría de errores genéricos.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|Representa la categoría de los errores causados por desbordamientos del sistema de bajo nivel.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Crea un objeto `error_code`.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Crea un objeto `error_condition`.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.|
|[operator<](../standard-library/system-error-operators.md#op_lt)|Prueba si un objeto es menor que el objeto pasado para la comparación.|
|[operator<<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>Enumeraciones

|||
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|Proporciona nombres simbólicos para todas las macros de código de error definidas por POSIX en `<errno.h>`.|

### <a name="classes-and-structs"></a>Clases y structs

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|Representa la base común abstracta para los objetos que describen una categoría de códigos de error.|
|[error_code](../standard-library/error-code-class.md)|Representa los errores de sistema de bajo nivel que son específicos de la implementación.|
|[error_condition](../standard-library/error-condition-class.md)|Representa los códigos de error definidos por el usuario.|
|[hash](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Representa un predicado de tipo que comprueba la enumeración [error_code (Clase)](../standard-library/error-code-class.md).|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Representa un predicado de tipo que comprueba la enumeración [error_condition (Clase)](../standard-library/error-condition-class.md).|
|[system_error](../standard-library/system-error-class.md)|Representa la clase base para todas las excepciones que se inician para notificar un desbordamiento del sistema de bajo nivel.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
