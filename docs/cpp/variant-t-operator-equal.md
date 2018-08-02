---
title: _variant_t::operator = | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d757c645ae131b88ffb99e571d1e08214eda8129
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462870"
---
# <a name="varianttoperator-"></a>_variant_t::operator =
**Específicos de Microsoft**  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_variant_t& operator=(  
   const VARIANT& varSrc   
);  
  
_variant_t& operator=(  
   const VARIANT* pVarSrc   
);  
  
_variant_t& operator=(  
   const _variant_t& var_t_Src   
);  
  
_variant_t& operator=(  
   short sSrc   
);  
  
_variant_t& operator=(  
   long lSrc   
);  
  
_variant_t& operator=(  
   float fltSrc   
);  
  
_variant_t& operator=(  
   double dblSrc   
);  
  
_variant_t& operator=(  
   const CY& cySrc   
);  
  
_variant_t& operator=(  
   const _bstr_t& bstrSrc   
);  
  
_variant_t& operator=(  
   const wchar_t* wstrSrc   
);  
  
_variant_t& operator=(  
   const char* strSrc   
);  
  
_variant_t& operator=(  
   IDispatch* pDispSrc   
);  
  
_variant_t& operator=(  
   bool bSrc   
);  
  
_variant_t& operator=(  
   IUnknown* pSrc   
);  
  
_variant_t& operator=(  
   const DECIMAL& decSrc   
);  
  
_variant_t& operator=(  
   BYTE bSrc   
);  
  
_variant_t& operator=(  
   char cSrc  
);  
  
_variant_t& operator=(  
   unsigned short usSrc  
);  
  
_variant_t& operator=(  
   unsigned long ulSrc  
);  
  
_variant_t& operator=(  
   int iSrc  
);  
  
_variant_t& operator=(  
   unsigned int uiSrc  
);  
  
_variant_t& operator=(  
   __int64 i8Src  
);  
  
_variant_t& operator=(  
   unsigned __int64 ui8Src  
);  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador asigna un nuevo valor al objeto `_variant_t`:  
  
-   **operador = (***varSrc***)** asigna existente `VARIANT` a un `_variant_t` objeto.  
  
-   **operador = (***pVarSrc***)** asigna existente `VARIANT` a un `_variant_t` objeto.  
  
-   **operador = (***var_t_Src***)** asigna existente `_variant_t` objeto a un `_variant_t` objeto.      
  
-   **operador = (***sSrc***)** asigna un **corto** valor entero a un `_variant_t` objeto.  
  
-   **operador = (**`lSrc`**)** asigna un **largo** valor entero a un `_variant_t` objeto.  
  
-   **operador = (***fltSrc***)** asigna un **float** valor numérico a un `_variant_t` objeto.  
  
-   **operador = (***dblSrc***)** asigna un **doble** valor numérico a un `_variant_t` objeto.  
  
-   **operador = (***cySrc***)** asigna un `CY` objeto a un `_variant_t` objeto.  
  
-   **operador = (***bstrSrc***)** asigna un `BSTR` objeto a un `_variant_t` objeto.  
  
-   **operador = (***wstrSrc***)** asigna una cadena Unicode a un `_variant_t` objeto.  
  
-   **operador = (**`strSrc`**)** asigna una cadena multibyte a un `_variant_t` objeto.  
  
-   **operador = (** `bSrc` **)** asigna un **bool** valor a un `_variant_t` objeto.  
  
-   **operador = (***pDispSrc***)** asigna un `VT_DISPATCH` objeto a un `_variant_t` objeto.  
  
-   **operador = (***pIUnknownSrc***)** asigna un `VT_UNKNOWN` objeto a un `_variant_t` objeto.  
  
-   **operador = (***decSrc***)** asigna un `DECIMAL` valor a un `_variant_t` objeto.  
  
-   **operador = (** `bSrc` **)** asigna un `BYTE` valor a un `_variant_t` objeto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)