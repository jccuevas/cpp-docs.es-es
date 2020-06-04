---
title: 'Tutorial: Análisis del código C/C++ para detectar defectos'
description: Muestra cómo usar el análisis de código con Microsoft C++ en Visual Studio.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: fe9b3775199b2a18cf940b99e87852350f1fbea9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370215"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Tutorial: Análisis del código C/C++ para detectar defectos

En este tutorial se muestra cómo analizar el código C/C++ para detectar posibles defectos de código. Utiliza las herramientas de análisis de código para el código C/C++.

En este tutorial,:

- Ejecute el análisis de código en código nativo.
- Analice las advertencias de defectos de código.
- Tratar la advertencia como un error.
- Anote el código fuente para mejorar el análisis de defectos de código.

## <a name="prerequisites"></a>Prerrequisitos

- Una copia del [ejemplo CppDemo](../code-quality/demo-sample.md).
- Comprensión básica de C/C++.

## <a name="run-code-analysis-on-native-code"></a>Ejecutar análisis de código en código nativo

### <a name="to-run-code-defect-analysis-on-native-code"></a>Para ejecutar el análisis de defectos de código en código nativo

::: moniker range=">=vs-2019"

1. Abra la solución CppDemo en Visual Studio.

     La solución CppDemo ahora rellena **el Explorador**de soluciones .

1. En el menú **Compilar** , elija **Reconstruir solución**.

     La solución se compila sin errores ni advertencias.

1. En el Explorador de **soluciones**, seleccione el proyecto CodeDefects.

1. En el menú **Proyecto** , elija **Propiedades**.

     Se muestra el cuadro de diálogo Páginas de propiedades **codeDefects.**

1. Seleccione la página de propiedades **Análisis** de código.

1. Cambie la propiedad **Habilitar análisis** de código en compilación a **Sí**. Elija **Aceptar** para guardar los cambios.

1. Vuelva a generar el proyecto CodeDefects.

     Las advertencias de análisis de código se muestran en la ventana **Lista** de errores.

::: moniker-end

::: moniker range="<=vs-2017"

1. Abra la solución CppDemo en Visual Studio.

     La solución CppDemo ahora rellena **el Explorador**de soluciones .

1. En el menú **Compilar** , elija **Reconstruir solución**.

     La solución se compila sin errores ni advertencias.

     > [!NOTE]
     > En Visual Studio 2017, es posible `E1097 unknown attribute "no_init_all"` que vea una advertencia falsa en el motor de IntelliSense. Puede omitir esta advertencia sin problemas.

1. En el Explorador de **soluciones**, seleccione el proyecto CodeDefects.

1. En el menú **Proyecto** , elija **Propiedades**.

     Se muestra el cuadro de diálogo Páginas de propiedades **codeDefects.**

1. Seleccione la página de propiedades **Análisis** de código.

1. Active la casilla Habilitar análisis de **código en compilación.** Elija **Aceptar** para guardar los cambios.

1. Vuelva a generar el proyecto CodeDefects.

     Las advertencias de análisis de código se muestran en la ventana **Lista** de errores.

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>Para analizar las advertencias de defectos de código

1. En el menú **Ver** , elija **Lista de errores**.

     Es posible que este elemento de menú no esté visible. Depende del perfil de desarrollador que elija en Visual Studio. Es posible que tenga que apuntar a **Otras ventanas** en el menú **Ver** y, a continuación, elija **Lista**de errores .

1. En la ventana **Lista** de errores, haga doble clic en la siguiente advertencia:

     C6230: Conversión implícita entre tipos semánticamente diferentes: uso de HRESULT en un contexto booleano.

     El editor de código muestra la línea `bool ProcessDomain()`que causó la advertencia dentro de la función. Esta advertencia indica `HRESULT` que se está utilizando a en una instrucción 'if' donde se espera un resultado booleano. Normalmente es un error, porque `S_OK` cuando el HRESULT se devuelve desde una función indica que `false`se ha realizado correctamente, pero cuando se convierte en un valor booleano se evalúa como .

1. Corrija esta advertencia `SUCCEEDED` mediante la macro, `true` que `HRESULT` se convierte en cuando un valor devuelto indica que se ha realizado correctamente. El código debe ser similar al código siguiente:

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. En la **lista de errores**, haga doble clic en la siguiente advertencia:

     C6282: Operador incorrecto: asignación de constante en contexto booleano. Considere la posibilidad de usar '' en su lugar.

1. Corrija esta advertencia probando la igualdad. El código debe tener un aspecto similar al código siguiente:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Corrija las advertencias C6001 restantes en `i` la `j` **lista** de errores inicializando y en 0.

1. Vuelva a generar el proyecto CodeDefects.

     El proyecto se compila sin advertencias ni errores.

## <a name="correct-source-code-annotation-warnings"></a>Advertencias de anotación de código fuente correctas

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>Para habilitar las advertencias de anotación de código fuente en annotation.c

::: moniker range=">=vs-2019"

1. En el Explorador de soluciones, seleccione el proyecto Anotaciones.

1. En el menú **Proyecto** , elija **Propiedades**.

     Se muestra el cuadro de diálogo Páginas de propiedades **de anotaciones.**

1. Seleccione la página de propiedades **Análisis** de código.

1. Cambie la propiedad **Habilitar análisis** de código en compilación a **Sí**. Elija **Aceptar** para guardar los cambios.

::: moniker-end

::: moniker range="<=vs-2017"

1. En el Explorador de soluciones, seleccione el proyecto Anotaciones.

1. En el menú **Proyecto** , elija **Propiedades**.

     Se muestra el cuadro de diálogo Páginas de propiedades **de anotaciones.**

1. Seleccione la página de propiedades **Análisis** de código.

1. Active la casilla Habilitar análisis de **código en compilación.** Elija **Aceptar** para guardar los cambios.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Para corregir las advertencias de anotación de código fuente en annotation.c

1. Vuelva a generar el proyecto Anotaciones.

1. En el menú **Generar** , elija Ejecutar análisis de **código en anotaciones**.

1. En la **lista de errores**, haga doble clic en la siguiente advertencia:

     C6011: Desreferenciación del puntero NULL 'newNode'.

     Esta advertencia indica un error por parte del autor de la llamada para comprobar el valor devuelto. En este caso, `AllocateNode` una llamada a podría devolver un NULL valor. Consulte el archivo de encabezado annotations.h para la declaración de función para `AllocateNode`.

1. El cursor se encuentra en la ubicación del archivo annotations.cpp donde se produjo la advertencia.

1. Para corregir esta advertencia, utilice una instrucción 'if' para probar el valor devuelto. El código debe ser similar al código siguiente:

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Vuelva a generar el proyecto Anotaciones.

     El proyecto se compila sin advertencias ni errores.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Utilice la anotación de código fuente para detectar más problemas

### <a name="to-use-source-code-annotation"></a>Para usar la anotación de código fuente

1. Anotar parámetros formales `AddTail` y valor devuelto de la función para indicar que los valores del puntero pueden ser nulos:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. En el menú **Compilar**, elija **Ejecutar análisis de código en la solución**.

1. En la **lista de errores**, haga doble clic en la siguiente advertencia:

     C6011: Desreferenciación del puntero NULL 'nodo'.

     Esta advertencia indica que el nodo pasado a la función podría ser null.

1. Para corregir esta advertencia, utilice una instrucción 'if' al principio de la función para probar el valor pasado. El código debe ser similar al código siguiente:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. En el menú **Compilar**, elija **Ejecutar análisis de código en la solución**.

     El proyecto ahora se compila sin advertencias ni errores.

## <a name="see-also"></a>Consulte también

[Tutorial: Análisis del código administrado para detectar defectos de código](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Análisis de código para C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
