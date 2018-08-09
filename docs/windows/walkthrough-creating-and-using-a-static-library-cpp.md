---
title: 'Tutorial: Crear y utilizar una biblioteca estática (C++) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f17bbe624497b9481977785ca555261826295c4
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015750"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Tutorial: Crear y utilizar una biblioteca estática (C++)
En este tutorial paso a paso se muestra cómo crear una biblioteca estática (archivo .lib) para su uso con aplicaciones de C++. Utilizar una biblioteca estática es una excelente manera de reutilizar el código. En lugar de volver a implementar las mismas rutinas en todos las aplicaciones que requieran la funcionalidad, escríbalas una vez en una biblioteca estática y, a continuación, haga referencia a ellas desde las aplicaciones. El código vinculado desde una biblioteca estática pasa a formar parte de la aplicación (no es necesario instalar otro archivo para utilizar el código).  
  
 En este tutorial se tratan las siguientes tareas:  
  
-   [Creación de un proyecto de biblioteca estática](#CreateLibProject)  
  
-   [Agregar una clase a la biblioteca estática](#AddClassToLib)  
  
-   [Crear una aplicación de consola haga referencia a la biblioteca estática](#CreateAppToRefTheLib)  
  
-   [Usar la funcionalidad de la biblioteca estática en la aplicación](#UseLibInApp)  
  
-   [Ejecución de la aplicación](#RunApp)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Descripción de los fundamentos del lenguaje C++.  
  
##  <a name="CreateLibProject"></a> Creación de un proyecto de biblioteca estática  
  
### <a name="to-create-a-static-library-project"></a>Para crear un proyecto de biblioteca estática  
  
1.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
2. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, expanda **instalado, Visual C++** y, a continuación, seleccione **Windows Desktop**.
  
3. En el panel central, seleccione **Asistente de escritorio de Windows**.  
  
4.  Especifique un nombre para el proyecto, por ejemplo, *MathFuncsLib*: en el **nombre** cuadro. Especifique un nombre para la solución, por ejemplo, *StaticLibrary*: en el **nombre de la solución** cuadro. Elija el botón **Aceptar** .  
  
5. En **tipo de aplicación**, seleccione la biblioteca estática (.lib).  
  
6. En **opciones adicionales**, desactive la **encabezado precompilado** casilla de verificación.
  
7. Elija **Aceptar** para crear el proyecto.  
 
##  <a name="AddClassToLib"></a> Agregar una clase a la biblioteca estática  
  
### <a name="to-add-a-class-to-the-static-library"></a>Para agregar una clase a la biblioteca estática  
  
1.  Si quiere crear un archivo de encabezado para una nueva clase, abra el menú contextual del proyecto **MathFuncsLib** en el **Explorador de soluciones**y después elija **Agregar**, **Nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , en el panel izquierdo, bajo **Visual C++**, seleccione **Código**. En el panel central, seleccione **Archivo de encabezado (.h)**. Especifique un nombre para el archivo de encabezado, por ejemplo, *MathFuncsLib.h*— y, a continuación, elija el **agregar** botón. Se muestra un archivo de encabezado en blanco.  
  
2.  Agregue una clase denominada `MyMathFuncs` para hacer operaciones matemáticas comunes, como suma, resta, multiplicación y división. El código debe ser similar a este:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  Para crear un archivo de código fuente para la nueva clase, abra el menú contextual para el proyecto **MathFuncsLib** en el **Explorador de soluciones**y después elija **Agregar**, **Nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , en el panel izquierdo, bajo **Visual C++**, seleccione **Código**. En el panel central, seleccione **Archivo de C++ (.cpp)**. Especifique un nombre para el archivo de origen, por ejemplo, *MathFuncsLib.cpp*— y, a continuación, elija el **agregar** botón. Se muestra un archivo de código fuente en blanco.  
  
4.  Use este archivo de código fuente para implementar la funcionalidad de **MyMathFuncs**. El código debe ser similar a este:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  Compile la biblioteca estática seleccionando **compilar** > **compilar solución** en la barra de menús. Esto crea una biblioteca estática que puede ser utilizada por otros programas.  
  
    > [!NOTE]
    >  Cuando compile desde la línea de comandos de Visual Studio, debe compilar el programa en dos pasos. En primer lugar, ejecute `cl /c /EHsc MathFuncsLib.cpp` para compilar el código y crear un archivo de objeto que se denomina `MathFuncsLib.obj`. (El comando `cl` invoca el compilador, Cl.exe y la opción `/c` especifica compilar sin vinculación. Para obtener más información, consulte [/c (compilar sin vincular)](../build/reference/c-compile-without-linking.md).) En segundo lugar, ejecute `lib MathFuncsLib.obj` para enlazar el código y crear la biblioteca estática `MathFuncsLib.lib`. (El comando `lib` invoca el Administrador de bibliotecas, Lib.exe. Para obtener más información, vea [LIB Reference](../build/reference/lib-reference.md)).  
  
##  <a name="CreateAppToRefTheLib"></a> Crear una aplicación de consola haga referencia a la biblioteca estática  
  
### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>Para crear una aplicación de consola C++ que haga referencia a la biblioteca estática  
  
1.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
2. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, expanda **instalado, Visual C++** y, a continuación, seleccione **Windows Desktop**.  

3. En el panel central, seleccione **Asistente de escritorio de Windows**.  
  
4.  Especifique un nombre para el proyecto, por ejemplo, *MyExecRefsLib*: en el **nombre** cuadro. En la lista desplegable junto a **Solución**, seleccione **Agregar a solución**. Esto agrega el nuevo proyecto a la solución que contiene la biblioteca estática. Elija el botón **Aceptar** .  
5. En **tipo de aplicación**, seleccione **aplicación de consola (.exe)**.

6. En **obtener opciones**, desactive la **encabezado precompilado** casilla de verificación.

7. Elija **Aceptar** para crear el proyecto.  
  
##  <a name="UseLibInApp"></a> Usar la funcionalidad de la biblioteca estática en la aplicación  
  
### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Para utilizar la funcionalidad de la biblioteca estática en la aplicación  
  
1.  Después de crear una aplicación de consola, se crea un programa vacío. El nombre del archivo de código fuente será el mismo que el elegido anteriormente. En este ejemplo, se llama `MyExecRefsLib.cpp`.  
  
2.  Para poder usar las rutinas de coincidencia de la biblioteca estática, debe hacer referencia a ella. Para ello, abra el menú contextual para el **MyExecRefsLib** proyecto **el Explorador de soluciones**y, a continuación, elija **agregar** > **referencia**.  
  
3.  El cuadro de diálogo **Agregar referencia** muestra las bibliotecas a las que puede hacer referencia. La pestaña **Proyectos** enumera los proyectos de la solución actual y las bibliotecas que contienen. En la pestaña **Proyectos** , active la casilla situada junto a **MathFuncsLib** y después elija el botón **Aceptar** .  
  
4.  Para hacer referencia a la `MathFuncsLib.h` archivo de encabezado, debe modificar la ruta de acceso de los directorios de inclusión. En el cuadro de diálogo **Páginas de propiedades** de **MyExecRefsLib**, expanda los nodos **Propiedades de configuración** y **C/C++** , y luego seleccione **General**. Junto a **Directorios de inclusión adicionales**, especifique la ruta de acceso del directorio **MathFuncsLib** o búsquela.  
  
     Para buscar la ruta del directorio abra el cuadro de lista desplegable del valor de propiedad y, a continuación, elija **Editar**. En el **directorios de inclusión adicionales** cuadro de diálogo, en el cuadro de texto, seleccione una línea en blanco y, a continuación, elija el botón de puntos suspensivos (**...** ) al final de la línea. En el cuadro de diálogo **Seleccionar directorio** , seleccione el directorio **MathFuncsLib** y después elija el botón **Seleccionar carpeta** para guardar la selección y cerrar el cuadro de diálogo. En el cuadro de diálogo **Directorios de inclusión adicionales** , elija el botón **Aceptar** y, en el cuadro de diálogo **Páginas de propiedades** , elija el botón **Aceptar** para guardar los cambios en el proyecto.  
  
5.  Ahora puede usar el `MyMathFuncs` clase en esta aplicación. Para ello, reemplace el contenido de `MyExecRefsLib.cpp` con este código:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  Compile el archivo ejecutable con **compilar** > **compilar solución** en la barra de menús.  
  
##  <a name="RunApp"></a> Ejecución de la aplicación  
  
### <a name="to-run-the-app"></a>Para ejecutar la aplicación  
  
1.  Asegúrese de que **MyExecRefsLib** esté seleccionado como proyecto predeterminado abriendo el menú contextual de **MyExecRefsLib** en el **Explorador de soluciones**y eligiendo **Establecer como proyecto de inicio**.  
  
2.  Para ejecutar el proyecto, en la barra de menús, elija **depurar** > **iniciar sin depurar**. El resultado debería ser similar a lo siguiente:  
  
    ```Output  
    a + b = 106.4  
    a - b = -91.6  
    a * b = 732.6  
    a / b = 0.0747475  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear y utilizar una biblioteca de vínculos dinámicos (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [Aplicaciones de escritorio (Visual C++)](../windows/desktop-applications-visual-cpp.md)