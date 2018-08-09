---
title: Estrategias de internacionalización | Microsoft Docs
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
ms.openlocfilehash: 1a3b8a47e70efa3268ae9b36eda311d267be2ded
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018934"
---
# <a name="internationalization-strategies"></a>Estrategias de internacionalización
Dependiendo de sus sistemas operativos de destino y mercados, tendrá varias estrategias de internacionalización:  
  
-   La aplicación usa Unicode.  
  
     Se utiliza la funcionalidad específica de Unicode y todos los caracteres tienen un ancho de 16 bits (aunque puede utilizar caracteres ANSI en algunas partes del programa para fines especiales). La biblioteca de tiempo de ejecución de C proporciona funciones, macros y tipos de datos para la programación exclusivas de Unicode. MFC es totalmente compatible con Unicode.  
  
-   La aplicación utiliza MBCS y se puede ejecutar en cualquier plataforma de Win32.  
  
     Use la funcionalidad específica de MBCS. Las cadenas pueden contener caracteres de byte único, los caracteres de doble byte o ambos. La biblioteca de tiempo de ejecución de C proporciona funciones, macros y tipos de datos para la programación solo MBCS. MFC está totalmente habilitado para MBCS.  
  
-   Se escribe el código fuente de la aplicación para la portabilidad completa, al volver a compilar con el símbolo `_UNICODE` o el símbolo `_MBCS` definido, puede generar versiones que usan alguno. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Utilice totalmente portables tipos C para funciones, macros y datos de tiempo de ejecución. La flexibilidad de MFC es compatible con cualquiera de estas estrategias.  
  
 El resto de estos temas centrarse en escribir código totalmente portable que se pueden compilar como Unicode o MBCS.  
  
## <a name="see-also"></a>Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Configuraciones regionales y páginas de códigos](../text/locales-and-code-pages.md)