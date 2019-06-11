---
title: Compatibilidad binaria de C++ entre Visual Studio 2015 y Visual Studio de 2019
ms.date: 05/03/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 052874eb9273ee9a9ce1695ffdadedd9911673e1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449031"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>Compatibilidad binaria de C++ entre Visual Studio 2015 y Visual Studio de 2019

En Visual Studio 2013 y versiones anteriores, no se garantizaba la compatibilidad binaria entre archivos objeto (OBJ), bibliotecas estáticas (LIB), bibliotecas dinámicas (DLL) y archivos ejecutables (EXE) compilados con versiones diferentes del conjunto de herramientas del compilador y las bibliotecas de tiempo de ejecución. 

En Visual Studio 2015 y versiones posteriores, el número principal del conjunto de herramientas de C++ es 14 (v140 en Visual Studio 2015, v141 en Visual Studio 2017 y v142 en Visual Studio 2019). Esto refleja el hecho de que las bibliotecas en tiempo de ejecución y las aplicaciones compiladas con cualquiera de las versiones del compilador muestran compatibilidad binaria. Esto significa que, si tiene una biblioteca de terceros compilada con Visual Studio 2015, no tendrá que volver a compilarla para consumirla desde una aplicación compilada con Visual Studio 2017 o con Visual Studio 2019.

La única excepción a esta regla es que las bibliotecas estáticas o los archivos objeto compilados con el modificador del compilador `/GL` no tienen compatibilidad binaria. 

Cuando se combinan archivos binarios compilados con diferentes versiones del conjunto de herramientas de MSVC, el elemento redistribuible de Visual C++ en el que la aplicación se ejecuta no puede ser anterior a ninguna de las versiones de conjunto de herramientas empleadas para compilar la aplicación o a ninguna biblioteca que consuma. 

## <a name="see-also"></a>Vea también

[Historial de cambios en Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
