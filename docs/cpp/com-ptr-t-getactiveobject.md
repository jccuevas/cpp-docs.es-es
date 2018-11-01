---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: 84e43de9c40baa3c596c68ed7739471c059cbac7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484505"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Específicos de Microsoft**

Se asocia a una instancia existente de un objeto dada una `CLSID` o `ProgID`.

## <a name="syntax"></a>Sintaxis

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>Parámetros

*rclsid*<br/>
El `CLSID` de un objeto.

*clsidString*<br/>
Una cadena Unicode que contiene un `CLSID` (empezando por "**{**") o un `ProgID`.

*clsidStringA*<br/>
Una cadena multibyte, en la página de códigos ANSI, que contiene un `CLSID` (empezando por "**{**") o un `ProgID`.

## <a name="remarks"></a>Comentarios

Estas funciones miembro llaman a **GetActiveObject** para recuperar un puntero a un objeto en ejecución que se ha registrado con OLE y, a continuación, el tipo de la interfaz de consultas para este puntero inteligente. El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`. `Release` se llama para disminuir el recuento de referencias para el puntero previamente encapsulado. Esta rutina devuelve el valor HRESULT para indicar éxito o error.

- **GetActiveObject (**`rclsid`**)** adjunta a una instancia existente de un objeto, dado un `CLSID`.

- **GetActiveObject (**`clsidString`**)** adjunta a una instancia existente de un objeto dada una cadena Unicode que contiene un `CLSID` (empezando por "**{**") o un `ProgID`.

- **GetActiveObject (**`clsidStringA`**)** adjunta a una instancia existente de un objeto dada una cadena de caracteres multibyte que contiene un `CLSID` (empezando por "**{**") o un `ProgID`. Las llamadas [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar), que se da por supuesto que es la cadena en la página de códigos ANSI en lugar de una página de códigos OEM.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)