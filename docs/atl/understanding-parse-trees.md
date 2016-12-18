---
title: "Understanding Parse Trees | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parse trees"
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Understanding Parse Trees
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede definir uno o más árboles de análisis sintácticos del script de registro, donde cada árbol de análisis tiene el siguiente formato:  
  
```  
<root key>{<registry expression>}+  
```  
  
 donde:  
  
```  
<root key> ::=  HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |  
               HKEY_LOCAL_MACHINE | HKEY_USERS |  
               HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |  
               HKEY_CURRENT_CONFIG | HKCR | HKCU |  
               HKLM | HKU | HKPD | HKDD | HKCC  
<registry expression> ::= <Add Key> | <Delete Key>  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
              [<Key Value>][{< Add Key>}]  
<Delete Key> ::=  Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```  
  
> [!NOTE]
>  `HKEY_CLASSES_ROOT` y `HKCR` son equivalentes; `HKEY_CURRENT_USER` y `HKCU` son equivalentes; etc.  
  
 Un árbol de análisis puede agregar claves y las subclaves múltiples a \<clave principal\> .  De esta manera, mantiene el identificador de una subclave abierta hasta que el analizador haya completado analizar todas las subclaves.  Este enfoque es más eficaz ejecutadas en una clave al mismo tiempo, como se muestra en el ejemplo siguiente:  
  
```  
HKEY_CLASSES_ROOT  
{  
   'MyVeryOwnKey'  
   {  
      'HasASubKey'  
      {  
         'PrettyCool?'  
      }  
   }  
}  
```  
  
 aquí, el registro abre inicialmente \(crea\) `HKEY_CLASSES_ROOT\MyVeryOwnKey`.  A continuación consulta que `MyVeryOwnKey` tiene una subclave.  En lugar de la clave para `MyVeryOwnKey`, el registro mantiene el identificador y abra \(crea\) `HasASubKey` mediante este identificador primario.  \(El sistema se puede ser más lento cuando no hay ningún identificador primario abierto.\) Así, abrir `HKEY_CLASSES_ROOT\MyVeryOwnKey` y `HasASubKey` a continuación que abre con `MyVeryOwnKey` como elemento primario es más rápido que `MyVeryOwnKey`que abre, `MyVeryOwnKey`se cierre, y `MyVeryOwnKey\HasASubKey`después de.  
  
## Vea también  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)