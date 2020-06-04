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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328498"
---
# <a name="kinds-of-dlls"></a>Tipos de archivos DLL

En este tema encontrará información que le ayudará a determinar el tipo de archivo DLL que le interesa compilar.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Diferentes tipos de archivos DLL disponibles

Con Visual Studio, puede compilar archivos DLL Win32 en C o C++ que no usen la biblioteca MFC (Microsoft Foundation Class). Puede crear un proyecto DLL que no esté basado en MFC con el Asistente para aplicaciones Win32.

Con el Asistente para archivos DLL de MFC, la biblioteca MFC está disponible en bibliotecas de vínculos estáticos o en diversos archivos DLL. Si el archivo DLL usa MFC, Visual Studio admite tres escenarios de desarrollo de archivos DLL:

- Compilar un archivo DLL de MFC estándar que vincula MFC estáticamente

- Compilar un archivo DLL de MFC estándar que vincula MFC dinámicamente

- Compilar un archivo DLL de extensión de MFC, que siempre vincula MFC dinámicamente

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [DLL no basada en MFC: información general](non-mfc-dlls-overview.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC: información general](extension-dlls-overview.md)

- [Tipo de archivo DLL que se va a usar](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a> Decidir qué tipo de archivo DLL se va a usar

Si el archivo DLL no usa MFC, recurra a Visual Studio para compilar un archivo DLL de Win32 que no esté basado en MFC. La vinculación del archivo DLL a MFC (estática o dinámicamente) ocupa un espacio considerable en disco y memoria. No debe vincular a MFC a menos que el archivo DLL use realmente MFC.

Si el archivo DLL va a usar MFC y lo van a emplear aplicaciones MFC o no basadas en MFC, debe compilar un archivo DLL de MFC estándar que vincule dinámicamente a MFC o bien uno que vincule estáticamente a MFC. En la mayoría de los casos, es probable que le interese usar un archivo DLL de MFC estándar que vincule dinámicamente a MFC, ya que el tamaño del archivo será mucho menor y el ahorro de memoria al usar la versión compartida de MFC puede ser considerable. Si vincula estáticamente a MFC, el tamaño del archivo DLL será mayor y podría ocupar memoria adicional, ya que carga su propia copia privada del código de la biblioteca MFC.

Es más rápido compilar un archivo DLL que vincula dinámicamente a MFC que uno que vincula estáticamente a MFC, ya que no es necesario vincular MFC en sí mismo. Esto es especialmente cierto en las compilaciones de depuración en las que el enlazador debe compactar la información de depuración. Al vincular con un archivo DLL que ya contiene la información de depuración, se debe compactar menos información de depuración en el archivo DLL.

Una desventaja de la vinculación dinámica a MFC es que debe distribuir los archivos DLL compartidos Mfcx0.dll y Msvcrxx.dll (o similares) con el archivo DLL. Los archivos DLL de MFC se pueden redistribuir libremente, pero aun así deben instalarse en el programa de instalación. Además, debe enviar el archivo Msvcrxx.dll, que contiene la biblioteca en tiempo de ejecución de C que usan tanto el programa como los archivos DLL de MFC.

Si solo van a usar el archivo DLL los ejecutables de MFC, podrá compilar un archivo DLL de MFC estándar o un archivo DLL de extensión de MFC. Si el archivo DLL implementa clases reutilizables derivadas de las clases MFC existentes, o si necesita pasar objetos derivados de MFC entre la aplicación y el archivo DLL, debe compilar un archivo DLL de extensión de MFC.

Si el archivo DLL vincula dinámicamente a MFC, los archivos DLL de MFC se pueden redistribuir con el archivo DLL. Esta arquitectura es especialmente útil para compartir la biblioteca de clases entre varios archivos ejecutables con el fin de ahorrar espacio en disco y minimizar el uso de memoria.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [DLL no basada en MFC: información general](non-mfc-dlls-overview.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC: información general](extension-dlls-overview.md)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
