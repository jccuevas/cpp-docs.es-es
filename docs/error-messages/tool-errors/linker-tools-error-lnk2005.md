---
title: Las herramientas del vinculador LNK2005 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: bf93f364b3dc7156a62eb1c474177eb7b85c7827
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2005"></a>Error de las herramientas del vinculador LNK2005
símbolo ya definido en objeto  
  
El `symbol` proporcionado, que se muestra en su forma representativa, se definió varias veces.  
  
Para más información, consulte los artículos de Knowledge Base:  
  
-   [Se produce un error de LNK2005 cuando la biblioteca CRT y bibliotecas MFC se vinculan en el orden incorrecto en Visual C++](https://support.microsoft.com/kb/148652)  
  
-   [CORRECCIÓN: Global Delete sobrecargado operador causas LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [Recibe errores LNK2005 cuando se compila un proyecto ejecutable (.exe) de ATL de Visual C++](https://support.microsoft.com/kb/184235).  
  
Este error se sigue el error irrecuperable [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Mezcla de bibliotecas estáticas y dinámicas cuando también se utiliza [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
2.  El símbolo es una función empaquetada (creada al compilar con [/Gy](../../build/reference/gy-enable-function-level-linking.md)) y se incluyó en más de un archivo, pero se cambió entre las compilaciones. Recompilar todos los archivos que incluyen `symbol`.  
  
3.  El símbolo está definido de manera distinta en dos objetos miembros de diferentes bibliotecas, y se utilizaron los dos objetos miembros.  
  
4.  Hay un valor absoluto definido dos veces, con un valor distinto en cada definición.  
  
5.  Un archivo de encabezado declaró y definió una variable. Entre las posibles soluciones están:  
  
    -   Declare la variable en. h: `extern BOOL MyBool;` y, a continuación, asignarle en un archivo .c o. cpp: `BOOL MyBool = FALSE;`.  
  
    -   Declarar la variable [estático](../../cpp/storage-classes-cpp.md#static).  
  
    -   Declarar la variable [selectany](../../cpp/selectany.md).  
  
6.  Si usa uuid.lib combinado con otros archivos .lib que definen GUID (por ejemplo, oledb.lib y adsiid.lib). Por ejemplo:  
  
    ```  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     Para corregirlo, agregue [/Force: Multiple](../../build/reference/force-force-file-output.md) a las opciones de línea de comandos del vinculador y compruebe que uuid.lib es la primera biblioteca de referencia.
