---
title: Funciones de &lt;system_error&gt;
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: ab4d0d1ee810df8f719bba762262eb03bf899408
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876290"
---
# <a name="ltsystem_errorgt-functions"></a>Funciones de &lt;system_error&gt;

## <a name="generic_category"></a>generic_category

Representa la categoría de errores genéricos.

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>Observaciones

El objeto `generic_category` es una implementación de [error_category](../standard-library/error-category-class.md).

## <a name="is_error_code_enum_v"></a>is_error_code_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a>is_error_condition_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a>make_error_code

Crea un objeto de código de error.

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>Parámetros

*error*\
Valor de enumeración de `std::errc` que se va a almacenar en el objeto de código de error.

### <a name="return-value"></a>Valor devuelto

El objeto de código de error.

### <a name="remarks"></a>Observaciones

## <a name="make_error_condition"></a>make_error_condition

Crea un objeto de la condición de error.

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>Parámetros

*error*\
Valor de enumeración de `std::errc` que se va a almacenar en el objeto de código de error.

### <a name="return-value"></a>Valor devuelto

El objeto de la condición de error.

### <a name="remarks"></a>Observaciones

## <a name="system_category"></a>system_category

Representa la categoría de los errores causados por desbordamientos del sistema de bajo nivel.

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>Observaciones

El objeto `system_category` es una implementación de [error_category](../standard-library/error-category-class.md).
