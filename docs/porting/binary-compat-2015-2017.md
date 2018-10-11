---
title: Compatibilidad binaria de C++ entre Visual Studio 2015 y Visual Studio de 2017 | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4cedef2d5343b93c544ab22c41d2e5ac661bc3dd
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169572"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Compatibilidad binaria de C++ entre Visual Studio 2015 y Visual Studio de 2017

En versiones anteriores de Visual Studio, no se garantizaba la compatibilidad binaria entre archivos de objeto (OBJ), bibliotecas estáticas (LIB), bibliotecas dinámicas (DLL) y archivos ejecutables (EXE) compilados con versiones diferentes del conjunto de herramientas del compilador y las bibliotecas de tiempo de ejecución. Esto ha cambiado en Visual Studio 2017. En Visual Studio 2015 y Visual Studio 2017, el número principal del conjunto de herramientas de C++ es 14 (v140 para Visual Studio 2015 y v141 para Visual Studio 2017). Esto refleja el hecho de que las bibliotecas en tiempo de ejecución y las aplicaciones compiladas con cualquiera de las versiones del compilador muestran —en su mayor parte— compatibilidad binaria. Por ejemplo, esto significa que si tiene un archivo DLL en Visual Studio 2015, no tiene que volver a compilarlo para consumirlo desde una aplicación compilada con Visual Studio 2017.  

Existen dos excepciones a esta regla. La compatibilidad binaria no se garantiza en estos casos:  

1. Cuando las bibliotecas estáticas o los archivos objeto se compilan con el modificador del compilador `/GL`.  

2. Al usar bibliotecas creadas con un conjunto de herramientas cuya versión es superior a la del conjunto de herramientas usado para compilar y vincular la aplicación. Por ejemplo, un programa que se compile y vincule con la versión de compilador 19.12 puede utilizar bibliotecas que se compilen con 19.0-19.12. Además, existe compatibilidad binaria solo entre Visual Studio 2015 y Visual Studio 2017; no se admite la vinculación de programas 19.x con las bibliotecas generadas por Visual Studio 2013 o versiones anteriores.

## <a name="see-also"></a>Vea también  

[Historial de cambios en Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)
