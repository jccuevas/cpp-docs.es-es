---
title: Compatibilidad binaria de C++ entre Visual Studio 2015 y Visual Studio de 2017 | Microsoft Docs
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d527a4e0647fe0e8471e168841a93512f4d1a9e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Compatibilidad binaria de C++ entre Visual Studio 2015 y Visual Studio de 2017


En versiones anteriores de Visual Studio, no se garantizaba la compatibilidad binaria entre archivos de objeto (OBJ), bibliotecas estáticas (LIB), bibliotecas dinámicas (DLL) y archivos ejecutables (EXE) compilados con versiones diferentes del conjunto de herramientas del compilador y las bibliotecas de tiempo de ejecución. Esto ha cambiado en Visual Studio 2017. En Visual Studio 2015 y Visual Studio 2017, el número principal del conjunto de herramientas de C++ es 14 (v140 para Visual Studio 2015 y v141 para Visual Studio 2017). Esto refleja el hecho de que las bibliotecas en tiempo de ejecución y las aplicaciones compiladas con cualquiera de las versiones del compilador muestran —en su mayor parte— compatibilidad binaria. Por ejemplo, esto significa que puede crear un archivo DLL en Visual Studio 2017 y usarlo en una aplicación compilada con Visual Studio 2015, o usar las bibliotecas redistribuibles de Visual Studio 2017 con una aplicación compilada mediante el conjunto de herramientas de 2015.  

Existen dos excepciones a esta regla. La compatibilidad binaria no se garantiza en estos casos:  

1) Cuando las bibliotecas estáticas o los archivos objeto se compilan con el modificador del compilador /GL.  

2) Cuando la aplicación usa bibliotecas redistribuibles cuyo número de versión es menor que el conjunto de herramientas que se utiliza para compilar la aplicación. En otras palabras, si se compila un programa con el conjunto de herramientas de plataforma v141, las bibliotecas redistribuibles que usa la aplicación deben compilarse con v141 o superior.  

## <a name="see-also"></a>Vea también  

[Historial de cambios en Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)


