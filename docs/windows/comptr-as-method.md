---
title: Método Comptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33f81412ef9580768269663aa23afe06ad4d62f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374688"
---
# <a name="comptras-method"></a>ComPtr::As (Método)

Devuelve un **ComPtr** objeto que representa la interfaz identificada por el parámetro de plantilla especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>Parámetros

*U*<br/>
La interfaz para ser representado por el parámetro *p*.

*p*<br/>
Un **ComPtr** objeto que representa la interfaz especificada por el parámetro *U*. Parámetro *p* no debe hacer referencia a la actual **ComPtr** objeto.

## <a name="remarks"></a>Comentarios

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización del asistente interno, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md) .

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ComPtr (clase)](../windows/comptr-class.md)