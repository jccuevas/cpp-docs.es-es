---
title: Tipos de archivos DLL
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: dae44d2dd39597420ce2a2c4e1642e8a7f0784e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328498"
---
# <a name="kinds-of-dlls"></a>Tipos de archivos DLL

En este tema se proporciona información para ayudarle a determinar el tipo de archivo DLL que se debe compilar.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>Diferentes tipos de DLL disponibles

Con Visual Studio, puede compilar archivos DLL de Win32 en C o C++ que no usen la biblioteca de Microsoft Foundation Class (MFC). Puede crear un proyecto DLL que no sea MFC con el Asistente para aplicaciones Win32.

La propia biblioteca MFC está disponible, ya sea en bibliotecas de vínculos estáticos o en un número de archivos DLL, con el Asistente para DLL de MFC. Si el archivo DLL usa MFC, Visual Studio admite tres escenarios de desarrollo de DLL diferentes:

- Creación de un archivo DLL de MFC normal que vincula estáticamente MFC

- Creación de un archivo DLL de MFC normal que vincula dinámicamente a MFC

- Creación de un archivo DLL de extensión MFC, que siempre vincula dinámicamente MFC

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Archivos DLL que no están basados en MFC: información general](non-mfc-dlls-overview.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC: información general](extension-dlls-overview.md)

- [Qué tipo de DLL usar](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>Decidir qué tipo de DLL usar

Si el archivo DLL no usa MFC, use Visual Studio para compilar un archivo DLL Win32 que no sea MFC. Vincular el archivo DLL a MFC (estática o dinámicamente) ocupa un espacio significativo en disco y memoria. No debe vincular a MFC a menos que el archivo DLL realmente usa MFC.

Si el archivo DLL usará MFC y lo usarán las aplicaciones MFC o no MFC, debe compilar un archivo DLL de MFC normal que se vincule dinámicamente a MFC o un archivo DLL de MFC normal que se vincule estáticamente a MFC. En la mayoría de los casos, es probable que desee usar un archivo DLL de MFC normal que se vincula dinámicamente a MFC porque el tamaño del archivo DLL será mucho menor y el ahorro en memoria por el uso de la versión compartida de MFC puede ser significativo. Si se vincula estáticamente a MFC, el tamaño del archivo DLL será mayor y potencialmente ocupará memoria adicional porque carga su propia copia privada del código de biblioteca MFC.

Crear un archivo DLL que se vincula dinámicamente a MFC es más rápido que crear un archivo DLL que se vincula estáticamente a MFC porque no es necesario vincular MFC sí mismo. Esto es especialmente cierto en compilaciones de depuración donde el vinculador debe compactar la información de depuración. Al vincular con un archivo DLL que ya contiene la información de depuración, hay menos información de depuración para compactar dentro del archivo DLL.

Una desventaja de vincular dinámicamente a MFC es que debe distribuir los archivos DLL compartidos Mfcx0.dll y Msvcrxx.dll (o archivos similares) con el archivo DLL. Los archivos DLL de MFC se pueden redistribuir libremente, pero debe instalar los archivos DLL en el programa de instalación. Además, debe enviar el archivo Msvcrxx.dll, que contiene la biblioteca en tiempo de ejecución de C que usa el programa y los propios archivos DLL de MFC.

Si el archivo DLL solo lo usarán los ejecutables de MFC, puede elegir entre compilar un archivo DLL de MFC normal o un archivo DLL de extensión MFC. Si el archivo DLL implementa clases reutilizables derivadas de las clases MFC existentes o necesita pasar objetos derivados de MFC entre la aplicación y el archivo DLL, debe compilar un archivo DLL de extensión MFC.

Si el archivo DLL se vincula dinámicamente a MFC, los archivos DLL de MFC se pueden redistribuir con el archivo DLL. Esta arquitectura es especialmente útil para compartir la biblioteca de clases entre varios archivos ejecutables para ahorrar espacio en disco y minimizar el uso de memoria.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Archivos DLL que no están basados en MFC: información general](non-mfc-dlls-overview.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC: información general](extension-dlls-overview.md)

## <a name="see-also"></a>Consulte también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
