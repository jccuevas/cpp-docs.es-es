---
title: 'Tutorial: Usar el nuevo MFC Shell controles | Microsoft Docs'
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 168d7c1740f9b33af1eca539e30514ce76259ceb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076339"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Tutorial: Usar los nuevos controles de Shell de MFC

En este tutorial, creará una aplicación similar al explorador de archivos. Creación de una ventana que tiene dos paneles. El panel de la izquierda contendrá un [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) objeto que muestra el escritorio en una vista jerárquica. El panel derecho contendrá un [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) que muestra los archivos en la carpeta que está seleccionada en el panel izquierdo.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se da por supuesto que ha configurado Visual Studio para usar **configuración General de desarrollo**. Si usa una configuración de desarrollo diferentes, algunas ventanas de Visual Studio que utilizamos en este tutorial no se muestren de forma predeterminada.

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Para crear una nueva aplicación MFC mediante el Asistente para aplicaciones MFC

1. Use la **MFC Application Wizard** para crear una nueva aplicación MFC. Para ejecutar el asistente, desde el **archivo** menú, seleccione **New**y, a continuación, seleccione **proyecto**. El **nuevo proyecto** se mostrará el cuadro de diálogo.

1. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C++** nodo en el **tipos de proyecto** panel y seleccione **MFC**. A continuación, en el **plantillas** panel, seleccione **aplicación MFC**. Escriba un nombre para el proyecto, como `MFCShellControls` y haga clic en **Aceptar**. Después de **MFC Application Wizard** muestra, use las siguientes opciones:

    1. En el **tipo de aplicación** panel, en **tipo de aplicación**, desactive la **documentos con fichas** opción. A continuación, seleccione **único documento** y seleccione **compatibilidad con la arquitectura documento/vista**. En **proyecto estilo**, seleccione **Visual Studio**y desde el **estilo Visual y colores** lista desplegable de la lista, seleccione **Office 2007 (tema azul)**.

    1. En el **compatibilidad con documentos compuestos** panel, seleccione **ninguno**.

    1. No realice ningún cambio a la **cadenas de plantillas de documento** panel.

    1. En el **soporte técnico de la base de datos** panel (Visual Studio 2015 y versiones posteriores), seleccione **ninguno** porque la aplicación no usa una base de datos.

    1. En el **características de la interfaz de usuario** panel, asegúrese de que el **usar una barra de menú y barra de herramientas** está seleccionada. Deje el resto de las opciones tal como están.

    1. En el **características avanzadas** panel, en **características avanzadas**, seleccione solo **controles ActiveX** y **manifiesto de controles comunes**. En **paneles de marco avanzados**, seleccione solo la **panel de navegación** opción. Lo hará que el asistente crear el panel a la izquierda de la ventana con un `CMFCShellTreeCtrl` ya insertado.

    1. No vamos a hacer cualquier cambio en el **clases generadas** panel, haga clic en **finalizar** para crear un nuevo proyecto MFC.

1. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, desde el **compilar** menú, seleccione **compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación seleccionando **Iniciar depuración** desde el **depurar** menú.

   El asistente crea automáticamente una aplicación que tiene una barra de menús estándar, una barra de herramientas estándar, una barra de estado estándar y una barra de Outlook a la izquierda de la ventana con un **carpetas** vista y un **calendario** vista .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Para agregar el control de lista de shell a la vista del documento

1. En esta sección, agregará una instancia de `CMFCShellListCtrl` a la vista que el asistente creó. Abra el archivo de encabezado de la vista haciendo doble clic en **MFCShellControlsView.h** en el **el Explorador de soluciones**.

   Busque la directiva `#pragma once` cerca de la parte superior del archivo de encabezado. Inmediatamente debajo de la directiva, agregue este código para incluir el archivo de encabezado para `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Agregue una variable miembro de tipo `CMFCShellListCtrl`. Primero, busque el siguiente comentario en el archivo de encabezado:

   ```cpp
   // Generated message map functions
   ```

   Inmediatamente antes del comentario, agregue este código:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. El **MFC Application Wizard** ya ha creado un `CMFCShellTreeCtrl` objeto en el `CMainFrame` un miembro protegido de la clase, pero. Se podrá tener acceso al objeto más adelante, cree ahora un descriptor de acceso para él. Abra el archivo de encabezado MainFrm.h haga doble clic en el **el Explorador de soluciones**. Localice el comentario siguiente:

   ```cpp
   // Attributes
   ```

   Inmediatamente debajo de él, agregue la declaración de método siguiente:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   A continuación, abra el archivo de código fuente MainFrm.cpp haga doble clic en el **el Explorador de soluciones**. En la parte inferior de ese archivo, agregue la definición de método siguiente:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Ahora vamos a actualizar la clase `CMFCShellControlsView` para controlar el mensaje de Windows `WM_CREATE`. Abra el **vista de clases** ventana y seleccione el `CMFCShellControlsView` clase. Haga clic en y seleccione **propiedades**.

    A continuación, en el **propiedades** ventana, haga clic en el **mensajes** icono. Desplácese hacia abajo hasta que encuentre el mensaje `WM_CREATE`. En la lista desplegable lista junto a `WM_CREATE`, seleccione  **\<Add > OnCreate**. El comando crea un controlador de mensajes para nosotros y actualiza automáticamente el mapa de mensajes MFC.

   En el `OnCreate` método, vamos a crear ahora nuestro `CMFCShellListCtrl` objeto. Busque la definición del método de `OnCreate` en el archivo de código fuente MFCShellControlsView.cpp y reemplace la implementación por el código siguiente:

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

1. Repita el paso anterior, esta vez para el mensaje `WM_SIZE`. Hará que la vista de las aplicaciones se rediseñe siempre que un usuario cambia el tamaño de la ventana de la aplicación. Reemplace la definición del método `OnSize` por el código siguiente:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. El último paso es conectar el `CMFCShellTreeCtrl` y `CMFCShellListCtrl` objetos mediante el uso de la [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) método. Después de llamar a `CMFCShellTreeCtrl::SetRelatedList`, `CMFCShellListCtrl` mostrará automáticamente el contenido del elemento seleccionado en el `CMFCShellTreeCtrl`. Nos conectamos a los objetos en el `OnActivateView` método, que se invalida desde [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   En el archivo de encabezado MFCShellControlsView.h, dentro de la declaración de clase de `CMFCShellControlsView`, agregue la declaración de método siguiente:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   A continuación, agregue la definición del método en el archivo de origen de la fuente MFCShellControlsView.cpp:

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

   Dado que estamos llamando a métodos de la `CMainFrame` (clase), debemos agregar un `#include` la directiva en la parte superior del archivo de origen fuente MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, desde el **compilar** menú, seleccione **compilar solución**. Si la aplicación se compila correctamente, puede ejecutarla seleccionando **Iniciar depuración** desde el **depurar** menú.

   Ahora deberían mostrarse los detalles del elemento seleccionado en el control `CMFCShellTreeCtrl` en el panel de vista. Al hacer clic en un nodo en `CMFCShellTreeCtrl`, `CMFCShellListCtrl` se actualizará automáticamente. Igualmente, si hace doble clic en una carpeta en `CMFCShellListCtrl`, `CMFCShellTreeCtrl` debe actualizarse automáticamente.

   Haga clic en cualquier elemento en el control de árbol o en el control de lista. Obtener el mismo menú contextual como si estuviera usando real **Explorador de archivos**.

## <a name="next-steps"></a>Pasos siguientes

- El Asistente para crea una barra de Outlook con ambos un **carpetas** panel y un **calendario** panel. Probablemente no tiene sentido tener un **calendario** panel en un **Explorer** ventana, así que vamos a quitarlo ahora.

- El `CMFCShellListCtrl` admite la visualización, como archivos de distintos modos, **iconos grandes**, **iconos pequeños**, **lista**, y **detalles**. Actualice la aplicación para implementar esta funcionalidad. Sugerencia: vea [ejemplos de Visual C++](../visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)
