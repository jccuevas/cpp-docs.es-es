---
title: Las herramientas del vinculador LNK1104 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 7fce9c60da4bceafb9ee81231a8630acb4397d83
ms.lasthandoff: 04/24/2017

---
# <a name="linker-tools-error-lnk1104"></a>Error de las herramientas del vinculador LNK1104
no se puede abrir el archivo '*filename*'  
  
El vinculador no pudo abrir el archivo especificado.  
  
Para corregir este error, compruebe las siguientes causas posibles:  
  
-   El archivo *nombre de archivo* no existe. Si el proyecto depende de otro proyecto para generar este archivo, asegúrese de que las dependencias del proyecto están establecidas correctamente.  
  
-   Al especificar bibliotecas en el cuadro de diálogo páginas de propiedades del proyecto, nombres de las bibliotecas deben estar separados por espacios, no por comas.  
  
-   El nombre de archivo o ruta de acceso especificada en la línea de comandos es incorrecta o la ruta de acceso tiene una especificación de unidad no válida. Compruebe la ortografía y el nombre de archivo y la ubicación. Si va a compilar un proyecto que se copió desde otro equipo, compruebe las rutas de acceso en la [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md) y actualizarlos si es necesario.  
  
-   No se instalan las bibliotecas para la configuración de proyecto o el conjunto de herramientas de plataforma. Compruebe que el conjunto de herramientas de plataforma y el SDK de Windows especificada en las páginas de propiedades para el proyecto está instalado y que incluye el conjunto de herramientas y bibliotecas necesarios para las opciones de configuración. Hay opciones de configuración independientes para configuraciones Debug y comercial, por lo que si uno funcionan las compilaciones, pero el otro produce un error, asegúrese de que la configuración es correcta y se instalan las herramientas necesarias para ambas configuraciones.  
  
-   No tiene suficiente espacio en disco. No es inusual para que el vinculador consumir una gran cantidad de espacio en disco temporal durante un vínculo.  
  
-   Tener permisos de archivo insuficientes para tener acceso a *filename*.  
  
-   La ruta de acceso *filename* se expande a más de 260 caracteres. Cambiar los nombres o reorganizar la estructura de directorios si es necesario para acortar las rutas de acceso a los archivos necesarios.  
  
-   Si el *filename* se denomina LNK*n*, que es un nombre de archivo generado por el vinculador para un archivo temporal, puede que no exista el directorio especificado en la variable de entorno TMP, o se puede especificar más de un directorio para la variable de entorno TMP. Debe especificarse solo una ruta de acceso para la variable de entorno TMP.  
  
-   Si el mensaje de error se produce para un nombre de biblioteca, y se portó recientemente el archivo .mak de un sistema de desarrollo de Microsoft Visual C++ anterior, es posible que la biblioteca ya no sea válida. Asegúrese de que el nombre de la biblioteca es correcto y que sigue existiendo en la ubicación especificada, o actualizar la ruta de acceso LIB para que apunte a la nueva ubicación.  
  
-   Puede que otro programa tenga el archivo abierto y que el enlazador no puede escribir en él. Los programas antivirus a menudo bloquean temporalmente el acceso a los archivos recién creados. Intente excluyendo los directorios de compilación de proyecto desde el programa antivirus.  
  
-   Tiene una variable de entorno LIB incorrecta. Para obtener información sobre cómo actualizar la variable de entorno LIB, vea [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md). Asegúrese de que los directorios que contienen las bibliotecas que necesita aparecen aquí.  
  
-   El enlazador usa archivos temporales en varios casos. Aunque tenga suficiente espacio en disco, un vínculo muy grande puede disminuir o fragmentar el espacio en disco disponible. Considere el uso de la [especificación /OPT (optimizaciones)](../../build/reference/opt-optimizations.md) opción; realizar lecturas de eliminación de comdat transitiva todos los archivos objeto varias veces.
