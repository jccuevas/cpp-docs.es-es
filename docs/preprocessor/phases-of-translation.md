---
title: "Fases de traducción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22d73156d4f03a32bd9aa382dd0cc610f8a5f03f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="phases-of-translation"></a>Fases de traducción
Los programas de C y C++ constan de uno o más archivos de código fuente, cada uno de los cuales contiene parte del texto de programa. Un archivo de código fuente, junto con sus archivos de inclusión (archivos que se incluyen mediante la directiva de preprocesador `#include`) pero sin incluir las secciones de código que se quitan mediante directivas de compilación condicional como `#if`, se denomina “unidad de traducción”.  
  
 Los archivos de código fuente se pueden traducir en momentos diferentes; de hecho, es común traducir solo los archivos actualizados. Las unidades de traducción traducidas se pueden procesar en archivos de objetos o bibliotecas de código de objetos independientes. Estas unidades de traducción independientes traducidas se vinculan para formar un programa ejecutable o una biblioteca de vínculos dinámicos (DLL).  Para obtener más información acerca de los archivos que puede usar como entrada al vinculador, vea [archivos de entrada de vínculo](../build/reference/link-input-files.md).  
  
 Las unidades de traducción pueden comunicarse mediante:  
  
-   Llamadas a funciones que tienen vinculación externa.  
  
-   Llamadas a funciones miembro de clase que tienen vinculación externa.  
  
-   Modificación directa de objetos que tienen vinculación externa.  
  
-   Modificación directa de archivos.  
  
-   Comunicación entre procesos (solo para aplicaciones basadas en Microsoft Windows).  
  
 La lista siguiente describe las fases en las que el compilador traduce los archivos:  
  
 *Asignación de caracteres*  
 Los caracteres del archivo de código fuente se asignan a la representación de código fuente interna. En esta fase, las secuencias de trígrafos se convierten en una representación interna de caracteres únicos.  
  
 *Delimitación de líneas*  
 Todas las líneas que terminan en una barra diagonal inversa (**\\**) y seguido inmediatamente por una nueva línea se combinan los caracteres con la siguiente línea en el archivo de origen formar líneas lógicas a partir de las líneas físicas. A menos que esté vacío, un archivo de código fuente debe finalizar en un carácter de nueva línea que no esté precedido por una barra diagonal inversa.  
  
 *División en tokens*  
 El archivo de código fuente se divide en tokens de preprocesamiento y caracteres de espacio en blanco. Cada uno de los comentarios del archivo de código fuente se reemplaza por un carácter de espacio. Los caracteres de nueva línea se conservan.  
  
 *Preprocesamiento*  
 Se ejecutan las directivas de preprocesamiento y se expanden las macros al archivo de código fuente. La instrucción `#include` invoca la traslación que comienza con los tres pasos anteriores de traslación en cualquier texto incluido.  
  
 *Asignación de juego de caracteres*  
 Todos los miembros y secuencias de escape de juego de caracteres de origen se convierten en sus equivalentes en el juego de caracteres de ejecución. Para Microsoft C y C++, tanto el juego de caracteres de ejecución de origen como el de ejecución son ASCII.  
  
 *Concatenación de cadenas*  
 Se concatenan todos los literales adyacentes de cadena y cadena de caracteres anchos. Por ejemplo, `"String " "concatenation"` se convierte en `"String concatenation"`.  
  
 *Traducción*  
 Todos los tokens se analizan sintáctica y semánticamente; estos tokens se convierten en código de objeto.  
  
 *Vinculación*  
 Se resuelven todas las referencias externas para crear un programa ejecutable o una biblioteca de vínculos dinámicos.  
  
 El compilador produce advertencias o errores durante las fases de traslación en las que encuentra errores de sintaxis.  
  
 El vinculador resuelve todas las referencias externas y crea un programa ejecutable o DLL combinando una o más unidades de traslación procesadas por separado junto con bibliotecas estándar.  
  
## <a name="see-also"></a>Vea también  
 [Preprocesador](../preprocessor/preprocessor.md)