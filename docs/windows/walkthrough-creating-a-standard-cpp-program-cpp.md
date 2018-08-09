---
title: 'Tutorial: Crear un programa estándar de C++ (C++) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vcfirstapp
- vccreatefirst
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0915f6f506b942a7ee52eec637c9ea6631339e79
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643288"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Tutorial: Crear un programa estándar de C++ (C++)
Puede usar Visual C++ en el entorno de desarrollo integrado (IDE) de Visual Studio para crear programas de C++ estándar. Siguiendo los pasos descritos en este tutorial, puede crear un proyecto, agregue un nuevo archivo al proyecto, modificar el archivo para agregar código de C++ y, a continuación, compilar y ejecutar el programa mediante [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Puede escribir su propio programa de C++ o utilizar uno de los programas de ejemplo. El programa de ejemplo en este tutorial es una aplicación de consola. Esta aplicación usa el `set` contenedor en la biblioteca estándar de C++.  
  
 Visual C++ cumple con el estándar de C++ de 2003, con estas excepciones principales: búsqueda de nombres en dos fases, especificaciones de excepciones y exportación. Además, Visual C++ admite varias características C ++ 0 x, por ejemplo, las expresiones lambda, auto, static_assert, referencias rvalue y plantillas extern.  
  
> [!NOTE]
>  Si se requiere compatibilidad con el estándar, use el `/Za` opción del compilador para deshabilitar las extensiones de Microsoft al estándar. Para obtener más información, consulte [/Za, /Ze (deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, debe comprender los conceptos básicos del lenguaje C++.  
  
### <a name="to-create-a-project-and-add-a-source-file"></a>Para crear un proyecto y agregar un archivo de origen  
  
1.  Cree un proyecto que apunta a **New** en el **archivo** menú y, a continuación, haga clic en **proyecto**.  
  
2.  En el **Visual C++** panel tipos de proyecto, haga clic en **Windows Desktop**y, a continuación, haga clic en **aplicación de consola Windows**.  
  
3.  Escriba un nombre para el proyecto.  
  
     De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente. También puede escribir una ubicación diferente para el proyecto.  
  
     Haga clic en **Aceptar** para crear el proyecto.  
  
4.  Si **el Explorador de soluciones** no aparece, en el **vista** menú, haga clic en **el Explorador de soluciones**.  
  
5.  Agregue un nuevo archivo de origen al proyecto, como sigue.  
  
    1.  En **el Explorador de soluciones**, haga clic en el **archivos de código fuente** carpeta, seleccione **agregar**y, a continuación, haga clic en **nuevo elemento**.  
  
    2.  En el **código** nodo, haga clic en **archivo C++ (.cpp)**, escriba un nombre para el archivo y, a continuación, haga clic en **agregar**.  
  
     El archivo .cpp aparece en la carpeta de archivos de código fuente en **el Explorador de soluciones**, y el archivo se abre en el editor de Visual Studio.  
  
6.  En el archivo en el editor, escriba un programa de C++ válido que usa la biblioteca estándar de C++ o copie uno de los programas de ejemplo y péguelo en el archivo.  
  
7.  Guarde el archivo.  
  
8. En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     El **salida** ventana muestra información sobre el progreso de la compilación, por ejemplo, la ubicación del registro de compilación y un mensaje que indica el estado de compilación.  
  
9. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  
  
     Si usa el programa de ejemplo, una ventana de comandos se muestra y se muestra si hay determinados enteros en el conjunto.  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [consola las aplicaciones en Visual C++](../windows/console-applications-in-visual-cpp.md). **A continuación:**[Tutorial: compilar un programa de C++ nativo en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)