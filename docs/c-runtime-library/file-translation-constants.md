---
title: "Constantes de traducción de archivo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.constants.file
dev_langs:
- C++
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e3005ebe8d36f77a470634b9fdd0003d9b6bb8d5
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="file-translation-constants"></a>Constantes de traducción de archivo
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas constantes especifican el modo de traducción (**"b"** o **"t"**). El modo se incluye en la cadena que especifica el tipo de acceso (**"r"**, **"w"**, **"a"**, **"r+"**, **"w+"**, **"a+"**).  
  
 Los modos de traducción son los siguientes:  
  
 **t**  
 Abre en modo de texto (traducido). En este modo, las combinaciones de retorno de carro-avance de línea (CR-LF) se convierten en avances de una línea (LF) en la entrada, y los caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura o lectura y escritura, `fopen` comprueba si aparece Ctrl+Z al final del archivo y lo quita, si es posible. Se hace así porque el uso de las funciones `fseek` y `ftell` para desplazarse por un archivo que finaliza con CTRL+Z puede hacer que `fseek` se comporte de manera incorrecta cerca del final del archivo.  
  
> [!NOTE]
>  La opción **t** no forma parte de la norma ANSI para `fopen` y `freopen`. Se trata de una extensión de Microsoft y no se debe usar si se desea disponer de portabilidad de ANSI.  
  
 **b**  
 Abre en modo binario (sin traducir). Las traducciones anteriores se suprimen.  
  
 Si no se especifica **t** o **b** en *mode*, el modo de traducción está definido por la variable de modo predeterminado [_fmode](../c-runtime-library/fmode.md). Para más información sobre el uso de los modos de texto y binario, vea [E/S de archivo en modo texto y en modo binario](../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="see-also"></a>Vea también  
 [_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)
