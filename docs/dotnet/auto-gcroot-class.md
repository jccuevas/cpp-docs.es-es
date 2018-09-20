---
title: auto_gcroot (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48412a932ff3752b0613f7045cd88992332b7917
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423238"
---
# <a name="autogcroot-class"></a>auto_gcroot (Clase)

Administración automática de recursos (como [auto_ptr (clase)](../standard-library/auto-ptr-class.md)) que se puede usar para insertar un identificador virtual en un tipo nativo.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename _element_type>
class auto_gcroot;
```

#### <a name="parameters"></a>Parámetros

*_element_type*<br/>
El tipo administrado que se va a incrustar.

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>Vea también

[auto_gcroot](../dotnet/auto-gcroot.md)<br/>
[auto_gcroot (Miembros)](../dotnet/auto-gcroot-members.md)<br/>
[Cómo: Declarar controladores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md)<br/>
[auto_handle (Clase)](../dotnet/auto-handle-class.md)