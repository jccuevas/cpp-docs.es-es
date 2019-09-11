---
title: 'Tutorial: Usar los nuevos controles de Shell de MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: cf0a6bd230364b48c78c72b8e453e7e641fb2d0e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907404"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Tutorial: Usar los nuevos controles de Shell de MFC

En este tutorial, creará una aplicación similar al explorador de archivos. Creará una ventana que tiene dos paneles. El panel izquierdo contendrá un objeto [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) que muestra el escritorio en una vista jerárquica. El panel derecho contendrá un [objeto cmfcshelllistctrl](../mfc/reference/cmfcshelllistctrl-class.md) que muestra los archivos de la carpeta que está seleccionada en el panel izquierdo.

## <a name="prerequisites"></a>Requisitos previos

- En Visual Studio 2017 y versiones posteriores, la compatibilidad con MFC es un componente opcional. Para instalarlo, abra el Instalador de Visual Studio desde el menú Inicio de Windows. Busque la versión de Visual Studio que está usando y elija el botón **modificar** . Asegúrese de que esté activada la casilla **desarrollo de escritorio con C++**  icono. En **componentes opcionales**, active el botón **compatibilidad con MFC** .

- En este tutorial se supone que ha configurado Visual Studio para usar la **configuración de desarrollo general**. Si utiliza una configuración de desarrollo diferente, es posible que algunas ventanas de Visual Studio que usamos en este tutorial no se muestren de forma predeterminada.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Para crear una nueva aplicación MFC mediante el Asistente para aplicaciones MFC

Estos pasos varían en función de la versión de Visual Studio que se use. Asegúrese de que el selector de versión en la esquina superior izquierda de esta página está establecido correctamente.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Para crear un proyecto MFC en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En el cuadro de búsqueda de la parte superior, escriba **MFC** y elija **aplicación MFC** en la lista de resultados. 

1. Haga clic en **Next**. En la página siguiente, escriba un nombre para el proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

   Una vez que se muestre el **Asistente para aplicaciones MFC** , use las siguientes opciones:
 
   1. Elija el **tipo de aplicación** a la izquierda. Después, seleccione **documento único** y seleccione **compatibilidad con arquitectura de documento/vista**. En **estilo del proyecto**, **Seleccione Visual Studio**y, en la lista desplegable **estilo visual y colores** , seleccione **Office 2007 (tema azul)** .

   1. En el panel **compatibilidad con documentos compuestos** , seleccione **ninguno**.

   1. No realice ningún cambio en el panel de propiedades de la **plantilla de documento** .

   1. En el panel características de la **interfaz de usuario** , asegúrese de que esté seleccionada la opción **usar una barra de menús y una barra de herramientas** . Deje el resto de las opciones tal como están.

   1. En el panel **características avanzadas** , seleccione **controles ActiveX**, **manifiesto de control común**y opción **Panel de navegación** . Deje todo lo demás como está. La opción **Panel de navegación** hará que el asistente cree el panel a la izquierda de la ventana con un `CMFCShellTreeCtrl` ya incrustado.

   1. No vamos a realizar ningún cambio en el panel **clases generadas** , así que haga clic en **Finalizar** para crear el nuevo proyecto MFC.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Para crear un proyecto MFC en Visual Studio 2017 o versiones anteriores

1. Utilice el **Asistente para aplicaciones MFC** para crear una nueva aplicación MFC. Para ejecutar el asistente, seleccione **nuevo**en el menú **archivo** y seleccione **proyecto**. Se mostrará el cuadro de diálogo **nuevo proyecto** .

1. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual C++**  en el panel **tipos de proyecto** y seleccione **MFC**. A continuación, en el panel **plantillas** , seleccione **aplicación MFC**. Escriba un nombre para el proyecto, `MFCShellControls` como y haga clic en **Aceptar**. 

   Una vez que se muestre el **Asistente para aplicaciones MFC** , use las siguientes opciones:

   1. En el panel **tipo de aplicación** , en tipo de **aplicación**, desactive la opción **documentos con pestañas** . A continuación, seleccione **documento único** y seleccione **compatibilidad con arquitectura de documento/vista**. En **estilo del proyecto**, **Seleccione Visual Studio**y, en la lista desplegable **estilo visual y colores** , seleccione **Office 2007 (tema azul)** .

   1. En el panel **compatibilidad con documentos compuestos** , seleccione **ninguno**.

   1. No realice cambios en el panel **cadenas de plantillas de documentos** .

   1. En el panel **compatibilidad con bases de datos** (Visual Studio 2015 y versiones anteriores), seleccione **ninguno** porque la aplicación no usa una base de datos.

   1. En el panel características de la **interfaz de usuario** , asegúrese de que esté seleccionada la opción **usar una barra de menús y una barra de herramientas** . Deje el resto de las opciones tal como están.

   1. En el panel **características avanzadas** , en **características avanzadas**, seleccione solo **controles ActiveX** y **manifiesto de control común**. En **paneles de marco avanzados**, seleccione solo la opción **Panel de navegación** . Hará que el asistente cree el panel a la izquierda de la ventana con un `CMFCShellTreeCtrl` ya incrustado.

   1. No vamos a realizar ningún cambio en el panel **clases generadas** , así que haga clic en **Finalizar** para crear el nuevo proyecto MFC.

::: moniker-end

Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú **compilar** , seleccione **compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación seleccionando **iniciar depuración** en el menú **depurar** .

El asistente crea automáticamente una aplicación con una barra de menús estándar, una barra de herramientas estándar, una barra de estado estándar y una barra de Outlook a la izquierda de la ventana con una vista de **carpetas** y una vista de **calendario** .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Para agregar el control de lista de shell a la vista del documento

1. En esta sección, agregará una instancia de `CMFCShellListCtrl` a la vista creada por el asistente. Abra el archivo de encabezado de vista haciendo doble clic en **MFCShellControlsView. h** en el **Explorador de soluciones**.

   Busque la directiva `#pragma once` cerca de la parte superior del archivo de encabezado. Inmediatamente debajo de la directiva, agregue este código para incluir el archivo de encabezado para `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Agregue una variable miembro de tipo `CMFCShellListCtrl`. Primero, busque el siguiente comentario en el archivo de encabezado:

   ```cpp
   // Generated message map functions
   ```

   Justo encima de ese comentario, agregue este código:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. El **Asistente para aplicaciones MFC** ya ha `CMFCShellTreeCtrl` creado un objeto `CMainFrame` en la clase, pero es un miembro protegido. Más adelante se tendrá acceso al objeto, por lo que ahora se crea un descriptor de acceso. Abra el archivo de encabezado MainFrm. h haciendo doble clic en él en el **Explorador de soluciones**. Localice el comentario siguiente:

   ```cpp
   // Attributes
   ```

   Inmediatamente debajo de él, agregue la declaración de método siguiente:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   A continuación, abra el archivo de origen MainFrm. cpp; para ello, haga doble clic en el **Explorador de soluciones**. En la parte inferior de ese archivo, agregue la definición de método siguiente:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Ahora vamos a actualizar la clase `CMFCShellControlsView` para controlar el mensaje de Windows `WM_CREATE`. Abra la ventana de **vista de clases** y seleccione `CMFCShellControlsView` la clase. Haga clic con el botón derecho y seleccione **propiedades**.

   A continuación, en el [Asistente para clases](reference/mfc-class-wizard.md), haga clic en la pestaña **mensajes** . Desplácese hacia abajo hasta que encuentre el mensaje `WM_CREATE`. En la lista desplegable lista junto a `WM_CREATE`, seleccione **\<Add > OnCreate**. El comando crea un controlador de mensajes para nosotros y actualiza automáticamente el mapa de mensajes de MFC.

   En el `OnCreate` método, ahora `CMFCShellListCtrl` crearemos el objeto. Busque la definición del método de `OnCreate` en el archivo de código fuente MFCShellControlsView.cpp y reemplace la implementación por el código siguiente:

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

1. Repita el paso anterior, esta vez para el mensaje `WM_SIZE`. Hará que se vuelva a dibujar la vista de aplicaciones cada vez que un usuario cambie el tamaño de la ventana de la aplicación. Reemplace la definición del método `OnSize` por el código siguiente:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. El último paso es conectar los `CMFCShellTreeCtrl` objetos y `CMFCShellListCtrl` mediante el método [CMFCShellTreeCtrl:: SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) . Después de llamar `CMFCShellTreeCtrl::SetRelatedList`a `CMFCShellListCtrl` , mostrará automáticamente el contenido del elemento seleccionado en `CMFCShellTreeCtrl`. Conectamos los objetos en el `OnActivateView` método, que se invalida desde [CView:: OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   En el archivo de encabezado MFCShellControlsView.h, dentro de la declaración de clase de `CMFCShellControlsView`, agregue la declaración de método siguiente:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   A continuación, agregue la definición del método al archivo de origen MFCShellControlsView. cpp:

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

   Dado que estamos llamando a métodos de `CMainFrame` la clase, debemos agregar una `#include` Directiva en la parte superior del archivo de origen MFCShellControlsView. cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú **compilar** , seleccione **compilar solución**. Si la aplicación se compila correctamente, ejecútela seleccionando **iniciar depuración** en el menú **depurar** .

   Ahora deberían mostrarse los detalles del elemento seleccionado en el control `CMFCShellTreeCtrl` en el panel de vista. Al hacer clic en un nodo en `CMFCShellTreeCtrl`, `CMFCShellListCtrl` se actualizará automáticamente. Igualmente, si hace doble clic en una carpeta en `CMFCShellListCtrl`, `CMFCShellTreeCtrl` debe actualizarse automáticamente.

   Haga clic con el botón secundario en cualquier elemento del control de árbol o del control de lista. Obtiene el mismo menú contextual que si usara el explorador de **archivos**real.

## <a name="next-steps"></a>Pasos siguientes

- El asistente creó una barra de Outlook con un panel de **carpetas** y un panel de **calendario** . Probablemente no tenga sentido tener un panel de **calendario** en una ventana del **Explorador** , por lo que debe quitar ese panel ahora.

- Admite `CMFCShellListCtrl` la visualización de archivos en modos diferentes, como **iconos grandes**, **iconos pequeños**, **lista**y **detalles**. Actualice la aplicación para implementar esta funcionalidad. Sugerencia: vea [ejemplos C++ visuales](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)
