---
title: _com_ptr_t::CreateInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa81e25b30061881dc00a401dc386647a8cdb73b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094239"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance

**Específicos de Microsoft**

Crea una nueva instancia de un objeto, dado un `CLSID` o `ProgID`.

## <a name="syntax"></a>Sintaxis

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>Parámetros

*rclsid*<br/>
El `CLSID` de un objeto.

*clsidString*<br/>
Una cadena Unicode que contiene un `CLSID` (empezando por "**{**") o un `ProgID`.

*clsidStringA*<br/>
Una cadena multibyte, en la página de códigos ANSI, que contiene un `CLSID` (empezando por "**{**") o un `ProgID`.

*dwClsContext*<br/>
Contexto para el código ejecutable.

*pOuter*<br/>
El desconocido externo para [agregación](../atl/aggregation.md).

## <a name="remarks"></a>Comentarios

Estas funciones de miembro llaman a `CoCreateInstance` para crear un nuevo objeto CM y, a continuación, consultas para el tipo de interfaz de este puntero inteligente. El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`. `Release` se llama para disminuir el recuento de referencias para el puntero previamente encapsulado. Esta rutina devuelve el valor HRESULT para indicar éxito o error.

- **CreateInstance (***rclsid* **,***dwClsContext***)** crea una nueva instancia de ejecución de un objeto, dado un `CLSID`.

- **CreateInstance (***clsidString* **,***dwClsContext***)** crea una nueva instancia de ejecución de un objeto dada una Cadena Unicode que contiene un `CLSID` (empezando por "**{**") o un `ProgID`.

- **CreateInstance (***clsidStringA* **,***dwClsContext***)** crea una nueva instancia de ejecución de un objeto dada una cadena de caracteres multibyte que contiene un `CLSID` (empezando por "**{**") o un `ProgID`. Las llamadas [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar), que se da por supuesto que es la cadena en la página de códigos ANSI en lugar de una página de códigos OEM.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)