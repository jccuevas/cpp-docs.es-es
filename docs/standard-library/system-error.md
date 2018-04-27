---
title: '&lt;system_error&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <system_error>
- system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 955a1c4f4b02c2ee5d1efc837585adf97be81ac1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltsystemerrorgt"></a>&lt;system_error&gt;

Incluya el encabezado \<system_error > para definir la clase de excepción `system_error` y relacionados con plantillas para el procesamiento de errores de sistema de bajo nivel.

## <a name="syntax"></a>Sintaxis

```cpp
#include <system_error>
```

### <a name="objects"></a>de la empresa

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Representa la categoría de errores genéricos.|
|[system_category](../standard-library/system-error-functions.md#system_category)|Representa la categoría de los errores causados por desbordamientos del sistema de bajo nivel.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[generic_errno](../standard-library/system-error-typedefs.md#generic_errno)|Un tipo que representa la enumeración que proporciona los nombres simbólicos para todas las macros de código de error definidas por Posix en `<errno.h>`.|

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Crea un objeto `error_code`.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Crea un objeto `error_condition`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.|
|[operator<](../standard-library/system-error-operators.md#op_lt)|Prueba si un objeto es menor que el objeto pasado para la comparación.|

### <a name="enumerations"></a>Enumeraciones

|||
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|Proporciona nombres simbólicos para todas las macros de código de error definidas por Posix en `<errno.h>`.|

### <a name="classes-and-structs"></a>Clases y structs

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|Representa la base común abstracta para los objetos que describen una categoría de códigos de error.|
|[error_code](../standard-library/error-code-class.md)|Representa los errores de sistema de bajo nivel que son específicos de la implementación.|
|[error_condition](../standard-library/error-condition-class.md)|Representa los códigos de error definidos por el usuario.|
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Representa un predicado de tipo que comprueba la enumeración [error_code (Clase)](../standard-library/error-code-class.md).|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Representa un predicado de tipo que comprueba la enumeración [error_condition (Clase)](../standard-library/error-condition-class.md).|
|[system_error](../standard-library/system-error-class.md)|Representa la clase base para todas las excepciones que se inician para notificar un desbordamiento del sistema de bajo nivel.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<system_error>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
