---
title: Tipos de archivos DLL
ms.date: 11/04/2016
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: f4aa8b1be7cd9ad32b10f12c5d1dfd3ae86adc1d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341775"
---
# <a name="kinds-of-dlls"></a>Tipos de archivos DLL

En este tema proporciona información para ayudarle a determinar el tipo de archivo DLL para compilar.

##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Diferentes tipos de archivo DLL disponibles

Con Visual C++, puede crear archivos DLL de Win32 en C o C++ que no usan la biblioteca Microsoft Foundation Class (MFC). Puede crear un proyecto de DLL que no son de MFC con el Asistente para aplicaciones Win32.

La misma biblioteca MFC está disponible, las bibliotecas de vínculos estáticos de o en un número de archivos DLL, con el Asistente para archivos DLL de MFC. Si el archivo DLL utiliza MFC, Visual C++ admite tres escenarios distintos de desarrollo de DLL:

- Creación de una DLL de MFC normal que estáticamente vincule a MFC

- Creación de una DLL de MFC normal que dinámicamente vincule a MFC

- Creación de un archivo DLL de extensión MFC, que siempre dinámicamente vincular MFC

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [DLL no basada en MFC: información general](non-mfc-dlls-overview.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC: información general](extension-dlls-overview.md)

- [Qué tipo de DLL utilicen](#_core_which_kind_of_dll_to_use)

##  <a name="_core_which_kind_of_dll_to_use"></a> Decidir qué tipo de archivo DLL que se usarán

Si no, el archivo DLL utiliza MFC, utilice Visual C++ para crear un archivo DLL para Win32 que no basado en MFC. Vinculación del archivo DLL a MFC (estática o dinámica) ocupa mucha memoria y mucho espacio en disco. No debe vincular a MFC a menos que realmente, el archivo DLL utiliza MFC.

Si el archivo DLL va a utilizar MFC y se usará en las aplicaciones MFC o no basados en MFC, deberá generar una DLL de MFC normal que se vincule dinámicamente a MFC o una DLL de MFC normal que se vincule estáticamente a MFC. En la mayoría de los casos, probablemente desee utilizar una DLL de MFC normal que se vincule dinámicamente a MFC, porque el tamaño del archivo del archivo DLL será mucho menor y el ahorro de memoria del uso de la versión compartida de MFC puede ser importante. Si vincula estáticamente a MFC, el tamaño del archivo del archivo DLL se mayor y posiblemente ocupará memoria adicional, ya que cargará su propia copia privada del código de biblioteca MFC.

Generar un archivo DLL que se vincule dinámicamente a MFC es más rápido que crear un archivo DLL que se vincule estáticamente a MFC porque no es necesario vincular MFC. Esto es especialmente cierto en las compilaciones de depuración que el vinculador debe compactar la información de depuración. Al vincular a un archivo DLL que ya contiene la información de depuración, hay menos información de depuración para compactar dentro de la DLL.

Una desventaja de vincularse dinámicamente a MFC es que debe distribuir los archivos DLL compartidos Mfcx0.dll y Msvcrxx.dll (o archivos similares) con el archivo DLL. Los archivos DLL de MFC son redistribuir libremente, pero todavía debe instalar los archivos DLL en el programa de instalación. Además, se debe enviar el archivo Msvcrxx.dll, que contiene la biblioteca de tiempo de ejecución de C que se usa tanto el programa y los mismos archivos DLL de MFC.

Si el archivo DLL sólo se usará en ejecutables MFC, tienen posibilidad de elegir entre crear un archivo DLL MFC o un archivo DLL de extensión MFC. Si el archivo DLL implementa clases reutilizables derivadas de las clases MFC existentes o si necesita pasar objetos derivados de MFC entre la aplicación y el archivo DLL, deberá generar un archivo DLL de extensión MFC.

Si el archivo DLL se vincula dinámicamente a MFC, se puede redistribuir los archivos DLL de MFC con el archivo DLL. Esta arquitectura es especialmente útil para compartir la biblioteca de clases entre varios archivos ejecutables para ahorrar espacio en disco y minimizar el uso de memoria.

Antes de la versión 4.0, Visual C++ sólo admitía dos tipos de archivos DLL que utilizaban MFC: USRDLL y AFXDLL. Archivos DLL de MFC estándar vinculados estáticamente a MFC tienen las mismas características que el archivo USRDLL anterior. Archivos DLL de extensión MFC tiene las mismas características que los archivos AFXDLL.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [DLL no basada en MFC: información general](non-mfc-dlls-overview.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC: información general](extension-dlls-overview.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](dlls-in-visual-cpp.md)
