---
title: Secuencias de caracteres | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: c097f213d790a992d12a8c358282a5340fce52c4
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="character-sequences"></a>Secuencias de caracteres
**ANSI 3.8.2** Asignación de secuencias de caracteres del archivo de código fuente  
  
 Las instrucciones de preprocesador utilizan el mismo juego de caracteres que las instrucciones del archivo de código fuente, con la excepción de que no se admiten secuencias de escape.  
  
 Así, para especificar una ruta de acceso para un archivo de inclusión, se usa una sola barra diagonal inversa:  
  
```  
#include "path1\path2\myfile"  
```  
  
 En el código fuente, se requieren dos barras diagonales inversas:  
  
```  
fil = fopen( "path1\\path2\\myfile", "rt" );  
```  
  
## <a name="see-also"></a>Vea también  
 [Preprocesar directivas](../c-language/preprocessing-directives.md)
