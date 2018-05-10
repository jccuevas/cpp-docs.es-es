---
title: Estrategias de internacionalización | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20e4d7b067daedcbc5ce065c096e561dbf932ac1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="internationalization-strategies"></a>Estrategias de internacionalización
Según los sistemas operativos de destino y los mercados, tiene varias estrategias de internacionalización:  
  
-   La aplicación usa Unicode.  
  
     Puede utilizar la funcionalidad específica de Unicode y todos los caracteres tienen un ancho de 16 bits (aunque se pueden utilizar caracteres ANSI en algunas partes del programa para fines especiales). La biblioteca de tiempo de ejecución de C proporciona funciones, macros y tipos de datos para programar solamente en Unicode. MFC está totalmente habilitado para Unicode.  
  
-   La aplicación utiliza MBCS y puede ejecutarse en cualquier plataforma de Win32.  
  
     Se utiliza la funcionalidad específica de MBCS. Las cadenas pueden contener caracteres de un solo byte, caracteres de doble byte o ambos. La biblioteca de tiempo de ejecución de C proporciona funciones, macros y tipos de datos para programar solamente en MBCS. MFC está totalmente habilitado para MBCS.  
  
-   Se escribe el código fuente de la aplicación para la portabilidad completa, al volver a compilar con el símbolo **_UNICODE** o el símbolo **_MBCS** definido, puede generar versiones que usan alguno. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Utilice totalmente portables tipos C de datos, macros y funciones de tiempo de ejecución. La flexibilidad de MFC es compatible con cualquiera de estas estrategias.  
  
 El resto de estos temas se centran en escribir código totalmente portable que se puede generar como Unicode o MBCS.  
  
## <a name="see-also"></a>Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Configuraciones regionales y páginas de códigos](../text/locales-and-code-pages.md)