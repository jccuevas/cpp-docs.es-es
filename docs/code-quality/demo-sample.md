---
title: Proyecto de ejemplo de C++ para el análisis de código
description: Cómo crear una solución de ejemplo para su uso en el tutorial de análisis de código para Microsoft C++ en Visual Studio.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: c2a1b8c80b7e7aebd1f1530c66ade5859b392028
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372062"
---
# <a name="sample-c-project-for-code-analysis"></a>Proyecto de ejemplo de C++ para el análisis de código

Los procedimientos siguientes muestran cómo crear el ejemplo para [Tutorial: Analizar código C/C++ para defectos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). El procedimiento crea:

- Una solución de Visual Studio denominada *CppDemo*.

- Un proyecto de biblioteca estática denominado *CodeDefects*.

- Un proyecto de biblioteca estática denominado *Anotaciones*.

Los procedimientos también proporcionan el código para el encabezado y los archivos *.cpp* para las bibliotecas estáticas.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Crear la solución CppDemo y el proyecto CodeDefects

::: moniker range=">=vs-2019"

1. Abra Visual Studio y seleccione **Crear un nuevo proyecto**

1. En el cuadro de diálogo **Crear un nuevo proyecto,** cambie el filtro de idioma a **C++**.

1. Seleccione **Asistente para escritorio** de Windows y elija el botón **Siguiente.**

1. En la página Configurar el **nuevo proyecto,** en el cuadro de texto Nombre del **proyecto,** escriba *CodeDefects*.

1. En el cuadro de texto Nombre de la **solución** , escriba *CppDemo*.

1. Seleccione **Create**.

1. En el cuadro de diálogo Proyecto de escritorio de **Windows,** cambie el **Tipo** de aplicación a **Biblioteca estática (.lib).**

1. En **Opciones adicionales**, seleccione **Proyecto vacío**.

1. Elija **Aceptar** para crear la solución y el proyecto.

::: moniker-end

::: moniker range="vs-2017"

1. Abra Visual Studio. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto,** seleccione **Visual C++** > Escritorio de **Windows**.

1. Seleccione **Asistente para escritorio**de Windows .

1. En el cuadro de texto **Nombre** , escriba *CodeDefects*.

1. En el cuadro de texto Nombre de la **solución** , escriba *CppDemo*.

1. Elija **Ok**.

1. En el cuadro de diálogo Proyecto de escritorio de **Windows,** cambie el **Tipo** de aplicación a **Biblioteca estática (.lib).**

1. En **Opciones adicionales**, seleccione **Proyecto vacío**.

1. Elija **Aceptar** para crear la solución y el proyecto.

::: moniker-end

::: moniker range="vs-2015"

1. Abra Visual Studio. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto,** seleccione **Plantillas** > **Visual C++** > **Win32**.

1. Seleccione Aplicación de **consola Win32**.

1. En el cuadro de texto **Nombre** , escriba *CodeDefects*.

1. En el cuadro de texto Nombre de la **solución** , escriba *CppDemo*.

1. Elija **Ok**.

1. En el cuadro de diálogo **Asistente para aplicaciones Win32,** elija el botón **Siguiente.**

1. Cambie el **tipo de aplicación** a Biblioteca **estática**.

1. En **Opciones adicionales**, anule la selección de Encabezado **precompilado**.

1. Elija **Finalizar** para crear la solución y el proyecto.

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Agregar el archivo de encabezado y código fuente al proyecto CodeDefects

1. En el Explorador de soluciones, expanda **CodeDefects**.

1. Haga clic con el botón derecho para abrir el menú contextual **de Archivos de encabezado**. Elija Add New Item ( **Agregar** > **nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione**Código** **Visual C++** > y, a continuación, seleccione Archivo de **encabezado (.h)**.

1. En el cuadro de edición **Nombre,** escriba *Bug.h*y, a continuación, elija el botón **Agregar.**

1. En la ventana de edición *de Bug.h*, seleccione y elimine el contenido.

1. Copie el código siguiente y péguelo en el archivo *Bug.h* en el editor.

    ```cpp
    #pragma once

    #include <windows.h>

    // Function prototypes
    bool CheckDomain(wchar_t const *);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. En el Explorador de soluciones, haga clic con el botón derecho para abrir el menú contextual **de Archivos**de origen . Elija Add New Item ( **Agregar** > **nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**.

1. En el cuadro de edición **Nombre,** escriba *Bug.cpp*y, a continuación, elija el botón **Agregar.**

1. Copie el código siguiente y péguelo en el archivo *Bug.cpp* en el editor.

    ```cpp
    #include "Bug.h"

    // the user account
    wchar_t g_userAccount[USER_ACCOUNT_LEN] = { L"domain\\user" };
    int len = 0;

    bool CheckDomain(wchar_t const* domain)
    {
        return (wcsnlen_s(domain, USER_ACCOUNT_LEN) > 0);
    }

    HRESULT ReadUserAccount()
    {
        return S_OK;
    }

    bool ProcessDomain()
    {
        wchar_t* domain = new wchar_t[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == L'\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = L'\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. En la barra de menús, elija **Archivo** > **Guardar todo**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Agregar el proyecto Annotations y configurarlo como una biblioteca estática

::: moniker range=">=vs-2019"

1. En el Explorador de soluciones, haga clic con el botón secundario en **CppDemo** para abrir el menú contextual. Elija **Agregar** > **nuevo proyecto**.

1. En el cuadro de diálogo **Agregar un nuevo proyecto,** seleccione **Asistente para escritorio**de Windows y, a continuación, elija el botón **Siguiente.**

1. En la página **Configure your new project (Configurar** el nuevo proyecto), en el cuadro de texto Project name **(Nombre** del proyecto), escriba *Annotations (Anotaciones)* y, a continuación, elija **Create (Crear).**

1. En el cuadro de diálogo Proyecto de escritorio de **Windows,** cambie el **Tipo** de aplicación a **Biblioteca estática (.lib).**

1. En **Opciones adicionales**, seleccione **Proyecto vacío**.

1. Elija **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2017"

1. En el Explorador de soluciones, haga clic con el botón secundario en **CppDemo** para abrir el menú contextual. Elija **Agregar** > **nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto,** seleccione **Visual C++** > **Windows Desktop**.

1. Seleccione **Asistente para escritorio**de Windows .

1. En el cuadro de texto **Nombre** , escriba *Anotaciones*y, a continuación, elija **Aceptar**.

1. En el cuadro de diálogo Proyecto de escritorio de **Windows,** cambie el **Tipo** de aplicación a **Biblioteca estática (.lib).**

1. En **Opciones adicionales**, seleccione **Proyecto vacío**.

1. Elija **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2015"

1. En el Explorador de soluciones, haga clic con el botón secundario en **CppDemo** para abrir el menú contextual. Elija **Agregar** > **nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto** , seleccione Visual **C++** > **Win32**.

1. Seleccione Aplicación de **consola Win32**.

1. En el cuadro de texto **Nombre,** escriba *Anotaciones*.

1. Elija **Ok**.

1. En el cuadro de diálogo **Asistente para aplicaciones Win32,** elija el botón **Siguiente.**

1. Cambie el **tipo de aplicación** a Biblioteca **estática**.

1. En **Opciones adicionales**, anule la selección de Encabezado **precompilado**.

1. Elija **Finalizar** para crear el proyecto.

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Agregar el archivo de encabezado y código fuente al proyecto Annotations

1. En el Explorador de soluciones, expanda **Anotaciones**.

1. Haga clic con el botón derecho para abrir el menú contextual **de Archivos** de encabezado en **Anotaciones**. Elija Add New Item ( **Agregar** > **nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione**Código** **Visual C++** > y, a continuación, seleccione Archivo de **encabezado (.h)**.

1. En el cuadro de edición **Nombre,** escriba *annotations.h*y, a continuación, elija el botón **Agregar.**

1. En la ventana de edición de *annotations.h*, seleccione y elimine el contenido.

1. Copie el código siguiente y péguelo en el archivo *annotations.h* en el editor.

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. En el Explorador de soluciones, haga clic con el botón derecho para abrir el menú contextual **de Archivos** de origen en **Anotaciones**. Elija Add New Item ( **Agregar** > **nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**.

1. En el cuadro de edición **Nombre,** escriba *annotations.cpp*y, a continuación, elija el botón **Agregar.**

1. Copie el código siguiente y péguelo en el archivo *annotations.cpp* en el editor.

    ```cpp
    #include "annotations.h"
    #include <malloc.h>

    _Ret_maybenull_ LinkedList* AllocateNode()
    {
        LinkedList* result = static_cast<LinkedList*>(malloc(sizeof(LinkedList)));
        return result;
    }

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. En la barra de menús, elija **Archivo** > **Guardar todo**.

La solución ya está completa y debe compilarse sin errores.

::: moniker range="vs-2017"

> [!NOTE]
> En Visual Studio 2017, es posible `E1097 unknown attribute "no_init_all"` que vea una advertencia falsa en el motor de IntelliSense. Puede omitir esta advertencia sin problemas.

::: moniker-end
