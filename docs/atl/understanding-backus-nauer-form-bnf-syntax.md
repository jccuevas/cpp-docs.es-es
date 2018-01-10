---
title: Registrador de ATL y Backus Nauer forman la sintaxis (BNF) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01d364313420c0a950f8eba222e3ae020fbd86cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>Comprender la sintaxis de Backus Nauer formulario (BNF)
Las secuencias de comandos utilizadas por el registrador de ATL se describen en este tema mediante la sintaxis BNF, que emplea la notación descrita en la tabla siguiente.  
  
|Convención/símbolos|Significado|  
|------------------------|-------------|  
|`::=`|Equivalente|  
|`&#124;`|O|  
|`X+`|Uno o más `X`s.|  
|`[X]`|`X` es opcional. Los delimitadores opcionales se denotan mediante `[]`.|  
|Cualquier **negrita** texto|Un literal de cadena.|  
|Cualquier *en cursiva* texto|Cómo construir el literal de cadena.|  
  
 Como se indica en la tabla anterior, los scripts del registrador utilizan literales de cadena. Estos valores son texto real que debe aparecer en la secuencia de comandos. La tabla siguiente describen los literales de cadena que se utiliza en una secuencia de comandos del registrador de ATL.  
  
|Literal de cadena|Acción|  
|--------------------|------------|  
|**ForceRemove**|Quita completamente la clave siguiente (si existe) y, a continuación, volver a crearla.|  
|**NoRemove**|No se elimina la clave siguiente durante la eliminación del registro.|  
|**Val**|Especifica que `<Key Name>` es en realidad un valor con nombre.|  
|**Eliminar**|Elimina la clave siguiente durante el registro.|  
|**s**|Especifica que el valor siguiente es una cadena (**REG_SZ**).|  
|**d**|Especifica que el valor siguiente es un **DWORD** (**REG_DWORD**).|  
|**m**|Especifica que el valor siguiente es un multistring (**REG_MULTI_SZ**).|  
|**b**|Especifica que el valor siguiente es un valor binario (**REG_BINARY**).|  
  
## <a name="bnf-syntax-examples"></a>Ejemplos de sintaxis BNF  
 Estos son algunos ejemplos de sintaxis para ayudarle a entender cómo funcionan los literales de cadena y la notación en una secuencia de comandos del registrador de ATL.  
  
### <a name="syntax-example-1"></a>Ejemplo de sintaxis 1  
  
```  
<registry expression> ::= <Add Key>  
```  
  
 Especifica que `registry expression` es equivalente a `Add Key`.  
  
### <a name="syntax-example-2"></a>Ejemplo de sintaxis 2  
  
```  
<registry expression> ::= <Add Key> | <Delete Key>  
```  
  
 Especifica que `registry expression` es equivalente al tipo `Add Key` o `Delete Key`.  
  
### <a name="syntax-example-3"></a>Ejemplo de sintaxis 3  
  
```  
<Key Name> ::= '<AlphaNumeric>+'  
```  
  
 Especifica que `Key Name` equivale a uno o varios `AlphaNumerics`.  
  
### <a name="syntax-example-4"></a>Ejemplo de sintaxis 4  
  
```  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
```  
  
 Especifica que `Add Key` es equivalente a `Key Name`y que los literales de cadena, `ForceRemove`, `NoRemove`, y `val`, son opcionales.  
  
### <a name="syntax-example-5"></a>Ejemplo de sintaxis 5  
  
```  
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0  
```  
  
 Especifica que `AlphaNumeric` es equivalente a cualquier carácter que no sea NULL.  
  
### <a name="syntax-example-6"></a>Ejemplo de sintaxis 6  
  
```  
val 'testmulti' = m 'String 1\0String 2\0'  
```  
  
 Especifica que el nombre de clave `testmulti` está formado por un valor multistring `String 1` y `String 2`.  
  
### <a name="syntax-example-7"></a>Ejemplo de sintaxis 7  
  
```  
val 'testhex' = d '&H55'  
```  
  
 Especifica que el nombre de clave `testhex` es un **DWORD** el valor hexadecimal 55 (85 decimal). Tenga en cuenta este formato se ajusta a la **& H** notación que se encuentra en las especificaciones de Visual Basic.  
  
## <a name="see-also"></a>Vea también  
 [Crear scripts del registrador](../atl/creating-registrar-scripts.md)

