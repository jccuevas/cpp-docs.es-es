---
title: "_variant_t::_variant_t | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::_variant_t"
  - "_variant_t._variant_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_variant_t (clase), constructor"
  - "_variant_t (método)"
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::_variant_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Construye un objeto `_variant_t`.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 *varSrc*  
 Un objeto **VARIANT** que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *pVarSrc*  
 Puntero a un objeto **VARIANT** que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *var\_t\_Src*  
 Un objeto `_variant_t` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `fCopy`  
 Si es false, el objeto **VARIANT** proporcionado se adjunta al nuevo objeto `_variant_t` sin crear una nueva copia mediante **VariantCopy**.  
  
 *ISrc, sSrc*  
 Un valor entero que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `vtSrc`  
 El **VARTYPE** para el nuevo objeto `_variant_t`.  
  
 *fltSrc, dblSrc*  
 Un valor numérico que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `cySrc`  
 Un objeto **CY** que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `bstrSrc`  
 Un objeto `_bstr_t` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *strSrc, wstrSrc*  
 Una cadena que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `bSrc`  
 Un valor `bool` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `pIUknownSrc`  
 Puntero de interfaz COM a un objeto **VT\_UNKNOWN** que se va a encapsular en el nuevo objeto `_variant_t`.  
  
 `pDispSrc`  
 Puntero de interfaz COM a un objeto **VT\_DISPATCH** que se va a encapsular en el nuevo objeto `_variant_t`.  
  
 `decSrc`  
 Un valor **DECIMAL** que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `bSrc`  
 Un valor **BYTE** que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `cSrc`  
 Un valor `char` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *usSrc*  
 Un valor **unsigned short** que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *ulSrc*  
 Un valor `unsigned long` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 `iSrc`  
 Un valor `int` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *uiSrc*  
 Un valor `unsigned int` que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *i8Src*  
 Un valor \_\_**int64** que se va a copiar en el nuevo objeto `_variant_t`.  
  
 *ui8Src*  
 Un valor **unsigned \_\_int64** que se va a copiar en el nuevo objeto `_variant_t`.  
  
## Comentarios  
  
-   **\_variant\_t\( \)** Construye un objeto `_variant_t` vacío, `VT_EMPTY`.  
  
-   **\_variant\_t\( VARIANT&**  *varSrc*  **\)** Construye un objeto `_variant_t` a partir de una copia del objeto **VARIANT**.  El tipo variant se conserva.  
  
-   **\_variant\_t\( VARIANT\***  *pVarSrc*  **\)** Construye un objeto `_variant_t` a partir de una copia del objeto **VARIANT**.  El tipo variant se conserva.  
  
-   **\_variant\_t\( \_variant\_t&**  *var\_t\_Src*  **\)** Construye un objeto `_variant_t` a partir de otro objeto `_variant_t`.  El tipo variant se conserva.  
  
-   **\_variant\_t\( VARIANT&**  *varSrc* **, bool**  `fCopy`  **\)** Construye un objeto `_variant_t` a partir de un objeto **VARIANT** existente.  Si `fCopy` es **false**, el objeto **VARIANT** se asocia al nuevo objeto sin crear una copia.  
  
-   **\_variant\_t\( short**  *sSrc* **, VARTYPE**  `vtSrc`  **\= VT\_I2 \)** Construye un objeto `_variant_t` de tipo `VT_I2` o `VT_BOOL` a partir de un valor entero **short**.  Cualquier otro **VARTYPE** produce un error `E_INVALIDARG`.  
  
-   **\_variant\_t\( long**  `lSrc` **, VARTYPE**  `vtSrc`  **\= VT\_I4 \)** Construye un objeto `_variant_t` de tipo `VT_I4`, `VT_BOOL` o `VT_ERROR` a partir de un valor entero **long**.  Cualquier otro **VARTYPE** produce un error `E_INVALIDARG`.  
  
-   **\_variant\_t\( float**  `fltSrc`  **\)** Construye un objeto `_variant_t` de tipo `VT_R4` a partir de un valor numérico **float**.  
  
-   **\_variant\_t\( double**  `dblSrc` **, VARTYPE**  `vtSrc`  **\= VT\_R8 \)** Construye un objeto `_variant_t` de tipo `VT_R8` o `VT_DATE` a partir de un valor numérico **double**.  Cualquier otro **VARTYPE** produce un error `E_INVALIDARG`.  
  
-   **\_variant\_t\( CY&**  `cySrc`  **\)** Construye un objeto `_variant_t` de tipo `VT_CY` a partir de un objeto **CY**.  
  
-   **\_variant\_t\( \_bstr\_t&**  `bstrSrc`  **\)** Construye un objeto `_variant_t` de tipo `VT_BSTR` a partir de un objeto `_bstr_t`.  Se asigna un nuevo `BSTR`.  
  
-   **\_variant\_t\( wchar\_t \*** *wstrSrc*  **\)** Construye un objeto `_variant_t` de tipo `VT_BSTR` a partir de una cadena Unicode.  Se asigna un nuevo `BSTR`.  
  
-   **\_variant\_t\( char\***  `strSrc`  **\)** Construye un objeto `_variant_t` de tipo `VT_BSTR` a partir de una cadena.  Se asigna un nuevo `BSTR`.  
  
-   **\_variant\_t\( bool**  `bSrc`  **\)** Construye un objeto `_variant_t` de tipo `VT_BOOL` a partir de un valor `bool`.  
  
-   **\_variant\_t\( IUnknown\***  `pIUknownSrc` **, bool**  `fAddRef`  **\= true \)** Construye un objeto `_variant_t` de tipo **VT\_UNKNOWN** a partir de un puntero de interfaz COM.  Si `fAddRef` es **true**, se llama a `AddRef` en el puntero de interfaz proporcionado para que coincida con la llamada a **Release** que se producirá cuando se destruya el objeto `_variant_t`.  Es decisión suya llamar a **Release** en el puntero de interfaz proporcionado.  Si `fAddRef` es **false**, este constructor toma la propiedad del puntero de interfaz proporcionado; no debe llamar a **Release** en el puntero de interfaz proporcionado.  
  
-   **\_variant\_t\( IDispatch\***  `pDispSrc` **, bool**  `fAddRef`  **\= true \)** Construye un objeto `_variant_t` de tipo **VT\_DISPATCH** a partir de un puntero de interfaz COM.  Si `fAddRef` es **true**, se llama a `AddRef` en el puntero de interfaz proporcionado para que coincida con la llamada a **Release** que se producirá cuando se destruya el objeto `_variant_t`.  Es decisión suya llamar a **Release** en el puntero de interfaz proporcionado.  Si **fAddRef** es false, este constructor toma la propiedad del puntero de interfaz proporcionado; no debe llamar a **Release** en el puntero de interfaz proporcionado.  
  
-   **\_variant\_t\( DECIMAL&**  `decSrc`  **\)** Construye un objeto `_variant_t` de tipo **VT\_DECIMAL** a partir de un valor **decimal**.  
  
-   **\_variant\_t\( BYTE**  `bSrc`  **\)** Construye un objeto `_variant_t` de tipo `VT_UI1` a partir de un valor **BYTE**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)