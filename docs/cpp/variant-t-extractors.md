---
title: "_variant_t (Extractores) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t.operatordouble"
  - "operatorlong"
  - "_variant_t::operator_bstr_t"
  - "operatordouble"
  - "_variant_t.operatorCY"
  - "operatorCY"
  - "_variant_t::operatorCY"
  - "_variant_t::operatordouble"
  - "operatorfloat"
  - "operatorBYTE"
  - "_variant_t.operatorDECIMAL"
  - "_variant_t::operatorlong"
  - "operatorIDispatch"
  - "_variant_t.operatorBYTE"
  - "operatorDECIMAL"
  - "_variant_t.operator_bstr_t"
  - "_variant_t::operatorDECIMAL"
  - "_variant_t.operatorIUnknown"
  - "_variant_t.operatorlong"
  - "_variant_t::operatorIDispatch"
  - "_variant_t::operatorIUnknown"
  - "operatorIUnknown"
  - "_variant_t.operatorbool"
  - "_variant_t::operatorBYTE"
  - "_variant_t.operatorfloat"
  - "operator_bstr_t"
  - "_variant_t::operatorbool"
  - "operatorshort"
  - "_variant_t::operatorshort"
  - "_variant_t::operatorfloat"
  - "_variant_t.operatorIDispatch"
  - "_variant_t.operatorshort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extractores, _variant_t (clase)"
  - "operador _bstr_t"
  - "operador bool"
  - "operador BYTE"
  - "operador CY"
  - "operador DECIMAL"
  - "operador double"
  - "operador float"
  - "operador IDispatch"
  - "operador IUnknown"
  - "operador long"
  - "operador SHORT"
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _variant_t (Extractores)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Extraen datos del objeto **VARIANT** encapsulado.  
  
## Sintaxis  
  
```  
  
      operator short( ) const;   
operator long( ) const;   
operator float( ) const;   
operator double( ) const;   
operator CY( ) const;   
operator _bstr_t( ) const;   
operator IDispatch*( ) const;   
operator bool( ) const;   
operator IUnknown*( ) const;   
operator DECIMAL( ) const;   
operator BYTE( ) const;  
operator VARIANT() const throw();  
operator char() const;  
operator unsigned short() const;  
operator unsigned long() const;  
operator int() const;  
operator unsigned int() const;  
operator __int64() const;  
operator unsigned __int64() const;  
```  
  
## Comentarios  
 Extraen datos sin formato del objeto **VARIANT** encapsulado.  Si **VARIANT** todavía no es del tipo adecuado, se usa **VariantChangeType** para intentar la conversión y, si no se produce, se genera un error:  
  
-   **operator short\( \)** Extrae un valor entero **short**.  
  
-   **operator long\( \)** Extrae un valor entero **long**.  
  
-   **operator float\( \)** Extrae un valor numérico **float**.  
  
-   **operator double\( \)** Extrae un valor entero **double**.  
  
-   **operator CY\( \)** Extrae un objeto **CY**.  
  
-   **operator bool\( \)** Extrae un valor `bool`.  
  
-   **operator DECIMAL\( \)** Extrae un valor **DECIMAL**.  
  
-   **operator BYTE\( \)** Extrae un valor **BYTE**.  
  
-   **operator \_bstr\_t\( \)** Extrae una cadena, que se encapsula en un objeto `_bstr_t`.  
  
-   **operator IDispatch\*\( \)** Extrae un puntero dispinterface de un objeto **VARIANT** encapsulado.  Se llama a `AddRef` en el puntero resultante, por lo que debe decidir si es conveniente llamar a **Release** para liberarlo.  
  
-   **operator IUnknown\*\( \)** Extrae un puntero de interfaz COM de un objeto **VARIANT** encapsulado.  Se llama a `AddRef` en el puntero resultante, por lo que debe decidir si es conveniente llamar a **Release** para liberarlo.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)