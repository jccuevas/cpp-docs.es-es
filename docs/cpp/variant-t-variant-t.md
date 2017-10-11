---
title: _variant_t::_variant_t | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::_variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6bd29401970d3beffcac6d29247138aa65d6a338
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="varianttvariantt"></a>_variant_t::_variant_t
**Específicos de Microsoft**  
  
 Construye un objeto `_variant_t`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      _variant_t( ) throw( );  
  
_variant_t(  
   const VARIANT& varSrc   
);  
  
_variant_t(  
   const VARIANT* pVarSrc   
);  
  
_variant_t(  
   const _variant_t& var_t_Src   
);  
  
_variant_t(  
   VARIANT& varSrc,  
   bool fCopy   
);  
  
_variant_t(  
   short sSrc,  
   VARTYPE vtSrc = VT_I2   
);  
  
_variant_t(  
   long lSrc,  
   VARTYPE vtSrc = VT_I4   
);  
  
_variant_t(  
   float fltSrc   
) throw( );  
  
_variant_t(  
   double dblSrc,  
   VARTYPE vtSrc = VT_R8   
);  
  
_variant_t(  
   const CY& cySrc   
) throw( );  
  
_variant_t(  
   const _bstr_t& bstrSrc   
);  
  
_variant_t(  
   const wchar_t *wstrSrc   
);  
  
_variant_t(  
   const char* strSrc   
);  
  
_variant_t(  
   IDispatch* pDispSrc,  
   bool fAddRef = true   
) throw( );  
  
_variant_t(  
   bool bSrc   
) throw( );  
  
_variant_t(  
   IUnknown* pIUknownSrc,  
   bool fAddRef = true   
) throw( );  
  
_variant_t(  
   const DECIMAL& decSrc   
) throw( );  
  
_variant_t(  
   BYTE bSrc   
) throw( );  
  
variant_t(  
   char cSrc  
) throw();  
  
_variant_t(  
   unsigned short usSrc  
) throw();  
  
_variant_t(  
   unsigned long ulSrc  
) throw();  
  
_variant_t(  
   int iSrc  
) throw();  
  
_variant_t(  
   unsigned int uiSrc  
) throw();  
  
_variant_t(  
   __int64 i8Src  
) throw();  
  
_variant_t(  
   unsigned __int64 ui8Src  
) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *varSrc*  
 A **VARIANT** objeto que se copiará en el nuevo `_variant_t` objeto.  
  
 *pVarSrc*  
 Puntero a un **VARIANT** objeto que se copiará en el nuevo `_variant_t` objeto.  
  
 *var_t_Src*  
 Un objeto `_variant_t` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `fCopy`  
 Si es false, suministrado **VARIANT** objeto está asociado a la nueva `_variant_t` objeto sin crear una nueva copia por **VariantCopy**.  
  
 *ISrc, sSrc*  
 Un valor entero que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `vtSrc`  
 El **VARTYPE** para el nuevo `_variant_t` objeto.  
  
 *fltSrc, dblSrc*  
 Un valor numérico que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `cySrc`  
 A **CY** objeto que se copiará en el nuevo `_variant_t` objeto.  
  
 `bstrSrc`  
 Un objeto `_bstr_t` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *strSrc, wstrSrc*  
 Una cadena que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `bSrc`  
 Un valor `bool` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `pIUknownSrc`  
 Puntero a interfaz COM a un **VT_UNKNOWN** objeto que va a encapsular en el nuevo `_variant_t` objeto.  
  
 `pDispSrc`  
 Puntero a interfaz COM a un **VT_DISPATCH** objeto que va a encapsular en el nuevo `_variant_t` objeto.  
  
 `decSrc`  
 A **DECIMAL** valor que se copiará en el nuevo `_variant_t` objeto.  
  
 `bSrc`  
 A **bytes** valor que se copiará en el nuevo `_variant_t` objeto.  
  
 `cSrc`  
 Un valor `char` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *usSrc*  
 A **entero corto sin signo** valor que se copiará en el nuevo `_variant_t` objeto.  
  
 *ulSrc*  
 Un valor `unsigned long` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `iSrc`  
 Un valor `int` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *uiSrc*  
 Un valor `unsigned int` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *i8Src*  
 Un __**int64** valor que se copiará en el nuevo `_variant_t` objeto.  
  
 *ui8Src*  
 Un **__int64 sin signo** valor que se copiará en el nuevo `_variant_t` objeto.  
  
## <a name="remarks"></a>Comentarios  
  
-   **_variant_t ()** construye vacío `_variant_t` objeto, `VT_EMPTY`.  
  
-   **_variant_t (VARIANT &***varSrc***)** construye una `_variant_t` objeto desde una copia de la **VARIANT** objeto.     El tipo variant se conserva.  
  
-   **_variant_t (variante\****pVarSrc***)** construye una `_variant_t` objeto desde una copia de la **VARIANT** objeto.     El tipo variant se conserva.  
  
-   **_variant_t (_variant_t &***var_t_Src***)** construye una `_variant_t` objeto desde otro `_variant_t` objeto.     El tipo variant se conserva.  
  
-   **_variant_t (VARIANT &***varSrc* **, bool**`fCopy`**)** construye una `_variant_t` objeto a partir de una existente ** VARIANT** objeto.       Si `fCopy` es **false**, **VARIANT** objeto se adjunta al nuevo objeto sin crear una copia.  
  
-   **_variant_t (corto***sSrc* **, VARTYPE**`vtSrc`**= VT_I2)** construye una `_variant_t` objeto del tipo `VT_I2` o `VT_BOOL` desde una **corto** valor entero.       Cualquier otro **VARTYPE** da como resultado un `E_INVALIDARG` error.  
  
-   **_variant_t (long** `lSrc` **, VARTYPE**`vtSrc`**= VT_I4)** construye una `_variant_t` objeto de tipo `VT_I4`, `VT_BOOL`, o `VT_ERROR` desde una **largo** valor entero.       Cualquier otro **VARTYPE** da como resultado un `E_INVALIDARG` error.  
  
-   **_variant_t (float**`fltSrc`**)** construye una `_variant_t` objeto de tipo `VT_R4` desde una **float** valor numérico.      
  
-   **_variant_t (double** `dblSrc` **, VARTYPE**`vtSrc`**= VT_R8)** construye una `_variant_t` objeto de tipo `VT_R8` o `VT_DATE` de un **doble** valor numérico.       Cualquier otro **VARTYPE** da como resultado un `E_INVALIDARG` error.  
  
-   **_variant_t (CY &**`cySrc`**)** construye una `_variant_t` objeto de tipo `VT_CY` desde una **CY** objeto.      
  
-   **_variant_t (_bstr_t &**`bstrSrc`**)** construye una `_variant_t` objeto de tipo `VT_BSTR` desde un `_bstr_t` objeto.     Se asigna un nuevo `BSTR`.  
  
-   **_variant_t (wchar_t \* ** *wstrSrc***)** construye una `_variant_t` objeto del tipo `VT_BSTR` de una cadena Unicode.   Se asigna un nuevo `BSTR`.  
  
-   **_variant_t (char\***`strSrc`**)** construye una `_variant_t` objeto del tipo `VT_BSTR` de una cadena.     Se asigna un nuevo `BSTR`.  
  
-   **_variant_t (bool**`bSrc`**)** construye una `_variant_t` objeto de tipo `VT_BOOL` desde un `bool` valor.      
  
-   **_variant_t (IUnknown\* ** `pIUknownSrc` **, bool**`fAddRef`**= true)** construye una `_variant_t` objeto del tipo **VT_UNKNOWN ** de un puntero de interfaz COM.       Si `fAddRef` es **true**, a continuación, `AddRef` se llama en el puntero de interfaz proporcionado para que coincida con la llamada a **versión** que se producirá cuando el `_variant_t` se destruye el objeto. Es decisión suya llamar a **versión** en el puntero de interfaz proporcionado. Si `fAddRef` es **false**, este constructor toma la propiedad del puntero de interfaz proporcionado; no debe llamar a **versión** en el puntero de interfaz proporcionado.  
  
-   **_variant_t (IDispatch\* ** `pDispSrc` **, bool**`fAddRef`**= true)** construye una `_variant_t` objeto del tipo **VT_DISPATCH ** de un puntero de interfaz COM.       Si `fAddRef` es **true**, a continuación, `AddRef` se llama en el puntero de interfaz proporcionado para que coincida con la llamada a **versión** que se producirá cuando el `_variant_t` se destruye el objeto. Es decisión suya llamar a **versión** en el puntero de interfaz proporcionado. Si **fAddRef** es false, este constructor toma la propiedad del puntero de interfaz proporcionado; no debe llamar a **versión** en el puntero de interfaz proporcionado.  
  
-   **_variant_t (DECIMAL &**`decSrc`**)** construye una `_variant_t` objeto de tipo **VT_DECIMAL** desde una **DECIMAL** valor.      
  
-   **_variant_t (BYTE**`bSrc`**)** construye una `_variant_t` objeto de tipo `VT_UI1` desde una **bytes** valor.      
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)
