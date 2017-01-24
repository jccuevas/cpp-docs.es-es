---
title: "_variant_t::operator = | Microsoft Docs"
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
  - "_variant_t.operator="
  - "_variant_t::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= (operador), con objetos específicos de Visual C++"
  - "operador =, variante"
  - "operator=, variante"
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
## Sintaxis  
  
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
  
## Comentarios  
 El operador asigna un nuevo valor al objeto `_variant_t`:  
  
-   **operator\=\(**  *varSrc*  **\)** Asigna un objeto **VARIANT** existente a un objeto `_variant_t`.  
  
-   **operator\=\(**  *pVarSrc*  **\)** Asigna un objeto **VARIANT** existente a un objeto `_variant_t`.  
  
-   **operator\=\(**  *var\_t\_Src*  **\)** Asigna un objeto `_variant_t` existente a un objeto `_variant_t`.  
  
-   **operator\=\(**  *sSrc*  **\)** Asigna un valor entero **short** a un objeto `_variant_t`.  
  
-   **operator\=\(**  `lSrc`  **\)** Asigna un valor entero **long** a un objeto `_variant_t`.  
  
-   **operator\=\(**  *fltSrc*  **\)** Asigna un valor numérico **float** a un objeto `_variant_t`.  
  
-   **operator\=\(**  *dblSrc*  **\)** Asigna un valor numérico **double** a un objeto `_variant_t`.  
  
-   **operator\=\(**  *cySrc*  **\)** Asigna un objeto **CY** a un objeto `_variant_t`.  
  
-   **operator\=\(**  *bstrSrc*  **\)** Asigna un objeto `BSTR` a un objeto `_variant_t`.  
  
-   **operator\=\(**  *wstrSrc*  **\)** Asigna una cadena Unicode a un objeto `_variant_t`.  
  
-   **operator\=\(**  `strSrc`  **\)** Asigna una cadena multibyte a un objeto `_variant_t`.  
  
-   **operator\=\(**  `bSrc` **\)** Asigna un valor `bool` a un objeto `_variant_t`.  
  
-   **operator\=\(**  *pDispSrc*  **\)** Asigna un objeto **VT\_DISPATCH** a un objeto `_variant_t`.  
  
-   **operator\=\(**  *pIUnknownSrc*  **\)** Asigna un objeto **VT\_UNKNOWN** a un objeto `_variant_t`.  
  
-   **operator\=\(**  *decSrc*  **\)** Asigna un valor **DECIMAL** a un objeto `_variant_t`.  
  
-   **operator\=\(**  `bSrc` **\)** Asigna un valor **BYTE** a un objeto `_variant_t`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)