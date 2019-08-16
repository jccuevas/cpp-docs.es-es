---
title: usesgetlasterror (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: b14316bd929f4b41b13a76c41e94b31b7534e9d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513884"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indica al llamador que, si se produce un error al llamar a esa función, el llamador puede llamar `GetLastError` a para recuperar el código de error.

## <a name="syntax"></a>Sintaxis

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Comentarios

El atributo **usesgetlasterror** C++ tiene la misma funcionalidad que el atributo MIDL [usesgetlasterror](/windows/win32/Midl/usesgetlasterror) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [idl_module](idl-module.md) para obtener un ejemplo de cómo usar **usesgetlasterror**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**Module** (atributo)|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)