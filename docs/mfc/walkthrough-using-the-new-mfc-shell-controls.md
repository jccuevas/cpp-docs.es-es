---
title: 'Tutorial: Usar los nuevos controles de Shell de MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 5786fbbf7ec9f31e7d895a96dae27b8fc95abda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360209"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Tutorial: Usar los nuevos controles de Shell de MFC

En este tutorial, creará una aplicación similar al Explorador de archivos. Creará una ventana que tiene dos paneles. El panel izquierdo contendrá un [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) objeto que muestra el escritorio en una vista jerárquica. El panel derecho contendrá un [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) que muestra los archivos de la carpeta seleccionada en el panel izquierdo.

## <a name="prerequisites"></a>Prerrequisitos

- En Visual Studio 2017 y versiones posteriores, la compatibilidad con MFC es un componente opcional. Para instalarlo, abra el instalador de Visual Studio desde el menú Inicio de Windows. Busque la versión de Visual Studio que está utilizando y elija el botón **Modificar.** Asegúrese de que el icono Desarrollo de **escritorio con C++** esté activado. En **Componentes opcionales**, compruebe el botón **Compatibilidad con MFC.**

- En este tutorial se supone que ha configurado Visual Studio para usar la configuración de **desarrollo general**. Si usa una configuración de desarrollo diferente, es posible que algunas ventanas de Visual Studio que usamos en este tutorial no se muestren de forma predeterminada.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Para crear una nueva aplicación MFC mediante el Asistente para aplicaciones MFC

Estos pasos varían en función de la versión de Visual Studio que esté utilizando. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Para crear un proyecto MFC en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En el cuadro de búsqueda en la parte superior, escriba **MFC** y, a continuación, elija **MFC App** en la lista de resultados.

1. Haga clic en **Siguiente**. En la página siguiente, escriba un nombre para el proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

   Después de que se muestre el **Asistente para aplicaciones MFC,** utilice las siguientes opciones:

   1. Elija **el tipo** de aplicación a la izquierda. A continuación, seleccione **Documento único** y seleccione Compatibilidad con la **arquitectura Dedocument/View**. En **Estilo**de proyecto , seleccione **Visual Studio**y, en la lista desplegable Estilo visual y **colores,** seleccione **Office 2007 (tema azul).**

   1. En el panel **Compatibilidad con documentos compuestos,** seleccione **Ninguno**.

   1. No realice ningún cambio en el panel Propiedades de plantilla de **documento.**

   1. En el panel Características de la **interfaz** de usuario, asegúrese de que la opción Usar una barra de **menús y una barra de herramientas** esté seleccionada. Deje el resto de las opciones tal como están.

   1. En el panel **Características avanzadas,** seleccione **controles ActiveX**, Manifiesto de **control común**y Opción de panel **de navegación.** Deja todo lo demás como está. La opción Panel de **navegación** hará que el asistente cree `CMFCShellTreeCtrl` el panel a la izquierda de la ventana con un ya incrustado.

   1. No vamos a realizar ningún cambio en el panel **Clases generadas,** así que haga clic en **Finalizar** para crear el nuevo proyecto MFC.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Para crear un proyecto MFC en Visual Studio 2017 o versiones anteriores

1. Utilice el **Asistente para aplicaciones MFC** para crear una nueva aplicación MFC. Para ejecutar el asistente, en el menú **Archivo,** seleccione **Nuevo**y, a continuación, seleccione **Proyecto**. Se mostrará el cuadro de diálogo **Nuevo proyecto.**

1. En el cuadro de diálogo **Nuevo proyecto** , expanda el nodo **Visual C++** en el panel Tipos de **proyecto** y seleccione **MFC**. A continuación, en el panel **Plantillas** , seleccione **Aplicación MFC**. Escriba un nombre para el `MFCShellControls` proyecto, por ejemplo, y haga clic en **Aceptar**.

   Después de que se muestre el **Asistente para aplicaciones MFC,** utilice las siguientes opciones:

   1. En el panel Tipo de **aplicación,** en **Tipo de aplicación**, desactive la opción **Documentos con pestañas.** A continuación, seleccione **Documento único** y seleccione **Compatibilidad con la arquitectura Document/View**. En **Estilo**de proyecto , seleccione **Visual Studio**y, en la lista desplegable Estilo visual y **colores,** seleccione **Office 2007 (tema azul).**

   1. En el panel **Compatibilidad con documentos compuestos,** seleccione **Ninguno**.

   1. No realice ningún cambio en el panel Cadenas de **plantilla** de documento.

   1. En el panel **Compatibilidad con bases** de datos (Visual Studio 2015 y versiones anteriores), seleccione **Ninguno** porque la aplicación no usa una base de datos.

   1. En el panel Características de la **interfaz** de usuario, asegúrese de que la opción Usar una barra de **menús y una barra de herramientas** esté seleccionada. Deje el resto de las opciones tal como están.

   1. En el panel **Características avanzadas,** en **Características avanzadas**, seleccione solo **controles ActiveX** y Manifiesto de **control común**. En Paneles de **marco avanzados**, seleccione solo la opción Panel de **navegación.** Hará que el asistente cree el panel a la `CMFCShellTreeCtrl` izquierda de la ventana con un ya incrustado.

   1. No vamos a realizar ningún cambio en el panel **Clases generadas,** así que haga clic en **Finalizar** para crear el nuevo proyecto MFC.

::: moniker-end

Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú **Compilar,** seleccione **Compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación seleccionando **Iniciar depuración** en el menú **Depurar.**

El asistente crea automáticamente una aplicación que tiene una barra de menús estándar, una barra de herramientas estándar, una barra de estado estándar y una barra de Outlook a la izquierda de la ventana con una vista **Carpetas** y una vista **Calendario.**

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Para agregar el control de lista de shell a la vista del documento

1. En esta sección, agregará una `CMFCShellListCtrl` instancia de la vista que creó el asistente. Abra el archivo de encabezado de vista haciendo doble clic en **MFCShellControlsView.h** en el Explorador de **soluciones**.

   Busque la directiva `#pragma once` cerca de la parte superior del archivo de encabezado. Inmediatamente debajo de la directiva, agregue este código para incluir el archivo de encabezado para `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Agregue una variable miembro de tipo `CMFCShellListCtrl`. Primero, busque el siguiente comentario en el archivo de encabezado:

   ```cpp
   // Generated message map functions
   ```

   Inmediatamente encima de ese comentario, agregue este código:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. El **Asistente para aplicaciones MFC** ya creó un `CMFCShellTreeCtrl` objeto en la `CMainFrame` clase, pero es un miembro protegido. Accederemos al objeto más adelante, así que cree un descriptor de acceso para él ahora. Abra el archivo de encabezado MainFrm.h haciendo doble clic en él en el **Explorador**de soluciones . Localice el comentario siguiente:

   ```cpp
   // Attributes
   ```

   Inmediatamente debajo de él, agregue la declaración de método siguiente:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   A continuación, abra el archivo de origen MainFrm.cpp haciendo doble clic en él en el **Explorador**de soluciones . En la parte inferior de ese archivo, agregue la definición de método siguiente:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Ahora vamos a actualizar la clase `CMFCShellControlsView` para controlar el mensaje de Windows `WM_CREATE`. Abra la ventana **Vista** `CMFCShellControlsView` de clases y seleccione la clase. Haga clic con el botón secundario y seleccione **Propiedades**.

   A continuación, en [el Asistente para clases](reference/mfc-class-wizard.md), `WM_CREATE` haga clic en la pestaña **Mensajes.** En la lista desplegable `WM_CREATE`situada junto a , seleccione ** \<Agregar> OnCreate**. El comando crea un controlador de mensajes para nosotros y actualiza automáticamente el mapa de mensajes MFC.

   En `OnCreate` el método, ahora crearemos nuestro `CMFCShellListCtrl` objeto. Busque la definición del método de `OnCreate` en el archivo de código fuente MFCShellControlsView.cpp y reemplace la implementación por el código siguiente:

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

1. Repita el paso anterior, esta vez para el mensaje `WM_SIZE`. Esto hará que la vista de aplicaciones se vuelva a dibujar cada vez que un usuario cambie el tamaño de la ventana de la aplicación. Reemplace la definición del método `OnSize` por el código siguiente:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. El último paso es `CMFCShellTreeCtrl` `CMFCShellListCtrl` conectar el y objetos mediante el [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) método. Después `CMFCShellTreeCtrl::SetRelatedList`de `CMFCShellListCtrl` llamar , el mostrará automáticamente el `CMFCShellTreeCtrl`contenido del elemento seleccionado en el archivo . Conectamos los objetos en el `OnActivateView` método, que se invalida desde [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   En el archivo de encabezado MFCShellControlsView.h, dentro de la declaración de clase de `CMFCShellControlsView`, agregue la declaración de método siguiente:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   A continuación, agregue la definición del método al archivo de origen MFCShellControlsView.cpp:

    ```cpp
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView)
    {
        if (bActivate&& AfxGetMainWnd() != NULL)
        {
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);
        }

        CView::OnActivateView(bActivate,
            pActivateView,
            pDeactiveView);
    }
    ```

   Dado que estamos llamando `CMainFrame` a métodos de `#include` la clase, debemos agregar una directiva en la parte superior del archivo de origen MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú **Compilar,** seleccione **Compilar solución**. Si la aplicación se compila correctamente, ejecútela seleccionando **Iniciar depuración en** el menú **Depurar.**

   Ahora deberían mostrarse los detalles del elemento seleccionado en el control `CMFCShellTreeCtrl` en el panel de vista. Al hacer clic en un nodo en `CMFCShellTreeCtrl`, `CMFCShellListCtrl` se actualizará automáticamente. Igualmente, si hace doble clic en una carpeta en `CMFCShellListCtrl`, `CMFCShellTreeCtrl` debe actualizarse automáticamente.

   Haga clic con el botón derecho en cualquier elemento del control de árbol o en el control de lista. Obtendrá el mismo menú contextual que si estuviera utilizando el **Explorador**de archivos real.

## <a name="next-steps"></a>Pasos siguientes

- El asistente creó una barra de Outlook con un panel **Carpetas** y un panel **Calendario.** Probablemente no tiene sentido tener un panel **Calendario** en una ventana **del Explorador,** así que quite ese panel ahora.

- Es `CMFCShellListCtrl` compatible con la visualización de archivos en diferentes modos, como **iconos grandes,** **iconos pequeños,** **lista**y **detalles**. Actualice la aplicación para implementar esta funcionalidad. Sugerencia: consulte Ejemplos de [Visual C++](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Consulte también

[Tutoriales](../mfc/walkthroughs-mfc.md)
