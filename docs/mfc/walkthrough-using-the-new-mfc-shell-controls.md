---
title: 'Tutorial: Usar el nuevo MFC Shell controles | Documentos de Microsoft'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: eebfc98af109bbcdb0e5c1b3b2b3bf517dd8b076
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122103"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Tutorial: Usar los nuevos controles de Shell de MFC

En este tutorial creará una aplicación similar al Explorador de archivos. Creará una ventana que contendrá dos paneles. El panel izquierdo contendrá un [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) objeto que muestra el escritorio en una vista jerárquica. El panel de la derecha contendrá un [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) que muestra los archivos en la carpeta que está seleccionada en el panel izquierdo.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se da por supuesto que ha configurado [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] usar **configuración General de desarrollo**. Si usa otra configuración de desarrollo, algunas ventanas de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] que utilizamos en este tutorial podrían no mostrarse de forma predeterminada.

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Para crear una nueva aplicación MFC mediante el Asistente para aplicaciones MFC

1. Use la **Asistente para aplicaciones MFC** para crear una nueva aplicación MFC. Para ejecutar el asistente desde el **archivo** menú, seleccione **New**y, a continuación, seleccione **proyecto**. El **nuevo proyecto** se mostrará el cuadro de diálogo.

2. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C++** nodo en el **tipos de proyecto** panel y seleccione **MFC**. A continuación, en la **plantillas** panel, seleccione **aplicación MFC**. Escriba un nombre para el proyecto, como `MFCShellControls` y haga clic en **Aceptar**. El **Asistente para aplicaciones MFC** se mostrará.

3. En el **Asistente para aplicaciones MFC** cuadro de diálogo, haga clic en **siguiente**. El **tipo de aplicación** se mostrará el panel.

4. En el **tipo de aplicación** panel, en **tipo de aplicación**, desactive el **documentos con fichas** opción. A continuación, seleccione **único documento** y seleccione **compatibilidad con la arquitectura documento/vista**. En **proyecto estilo**, seleccione **Visual Studio**y desde el **estilo Visual y colores** de lista desplegable de la lista, seleccione **Office 2007 (tema azul)**. Deje el resto de las opciones tal como están. Haga clic en **siguiente** para mostrar la **compatibilidad con documentos compuestos** panel.

5. En el **compatibilidad con documentos compuestos** panel, seleccione **ninguno**. Haga clic en **siguiente** para mostrar la **cadenas de plantillas de documento** panel.

6. No realice cambios en el **cadenas de plantillas de documento** panel. Haga clic en **siguiente** para mostrar la **compatibilidad de base de datos** panel.

7. En el **compatibilidad de base de datos** panel, seleccione **ninguno** porque esta aplicación no usa una base de datos. Haga clic en **siguiente** para mostrar la **características de la interfaz de usuario** panel.

8. En el **características de la interfaz de usuario** panel, asegúrese de que el **usar una barra de menús y barra de herramientas** opción está seleccionada. Deje el resto de las opciones tal como están. Haga clic en **siguiente** para mostrar la **características avanzadas** panel.

9. En el **características avanzadas** panel, en **características avanzadas**, seleccione solo **controles ActiveX** y **manifiesto de controles comunes**. En **paneles de marco avanzados**, seleccione solo la **panel de navegación** opción. Esto hará que el asistente cree el panel a la izquierda de la ventana con un control `CMFCShellTreeCtrl` ya insertado. Haga clic en **siguiente** para mostrar la **clases generadas** panel.

10. No vamos a realizar los cambios realizados en el **clases generadas** panel. Por lo tanto, haga clic en **finalizar** para crear un nuevo proyecto MFC.

11. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, desde el **generar** menú, seleccione **generar solución**. Si la aplicación se compila correctamente, ejecute la aplicación seleccionando **Iniciar depuración** desde el **depurar** menú.

   El asistente crea automáticamente una aplicación que tiene una barra de menús estándar, una barra de herramientas estándar, una barra de estado estándar y una barra de Outlook a la izquierda de la ventana con un **carpetas** vista y un **calendario** vista .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Para agregar el control de lista de shell a la vista del documento

1. En esta sección, agregará una instancia de `CMFCShellListCtrl` a la vista que el asistente creó. Abra el archivo de encabezado de la vista haciendo doble clic en MFCShellControlsView.h en el **el Explorador de soluciones**.

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

2. El **Asistente para aplicaciones MFC** ya se ha creado un `CMFCShellTreeCtrl` objeto en el `CMainFrame` clase, pero es un miembro protegido. Tendremos acceso a este objeto más adelante. Por consiguiente, cree ahora un descriptor de acceso para él. Para abrir el archivo de encabezado MainFrm.h, haga doble clic en el **el Explorador de soluciones**. Localice el comentario siguiente:

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

3. Ahora vamos a actualizar el `CMFCShellControlsView` clase para administrar la **WM_CREATE** mensaje de windows. Abra el archivo de encabezado MFCShellControlsView.h y haga clic en esta línea de código:

    ```cpp
    class CMFCShellControlsView : public CView
    ```

   Después, en la **propiedades** ventana, haga clic en el **mensajes** icono. Desplácese hacia abajo hasta que encuentre el **WM_CREATE** mensaje. En la lista desplegable de la lista situada junto a **WM_CREATE**, seleccione  **\<Add > OnCreate**. De esta forma se crea un controlador de mensajes y se actualiza automáticamente el mapa de mensajes de MFC.

   En el método `OnCreate` vamos a crear ahora nuestro propio objeto `CMFCShellListCtrl`. Busque la definición del método de `OnCreate` en el archivo de código fuente MFCShellControlsView.cpp y reemplace la implementación por el código siguiente:

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

4. Repita el paso anterior, pero para la **WM_SIZE** mensaje. Esto hará que la vista de las aplicaciones se rediseñe siempre que un usuario cambie el tamaño de la ventana de la aplicación. Reemplace la definición del método `OnSize` por el código siguiente:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

5. El último paso consiste en conectar los `CMFCShellTreeCtrl` y `CMFCShellListCtrl` objetos mediante el uso de la [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) método. Después de llamar a este método, `CMFCShellListCtrl` mostrará automáticamente el contenido del elemento seleccionado en `CMFCShellTreeCtrl`. Se hará en el `OnActivateView` método, que se invalide de [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   En el archivo de encabezado MFCShellControlsView.h, dentro de la declaración de clase de `CMFCShellControlsView`, agregue la declaración de método siguiente:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   A continuación, agregue la definición de este método al archivo de código fuente MFCShellControlsView.cpp:

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

   Dado que llamamos a los métodos desde la clase `CMainFrame`, debemos agregar una directiva `#include` en la parte superior del archivo de código fuente MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

6. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, desde el **generar** menú, seleccione **generar solución**. Si la aplicación se compila correctamente, ejecute seleccionando **Iniciar depuración** desde el **depurar** menú.

   Ahora deberían mostrarse los detalles del elemento seleccionado en el control `CMFCShellTreeCtrl` en el panel de vista. Al hacer clic en un nodo en `CMFCShellTreeCtrl`, `CMFCShellListCtrl` se actualizará automáticamente. Igualmente, si hace doble clic en una carpeta en `CMFCShellListCtrl`, `CMFCShellTreeCtrl` debe actualizarse automáticamente.

   Haga clic con el botón secundario en cualquier elemento del control de árbol o del control de lista. Observe que obtiene el mismo menú contextual que si utilizara el Explorador de archivos auténtico.

## <a name="next-steps"></a>Pasos siguientes

- El asistente creó una barra de Outlook con un **carpetas** panel y un **calendario** panel. Probablemente no tiene sentido tener un **calendario** panel en una ventana del explorador. Por consiguiente, vamos a quitarlo ahora.

- El `CMFCShellListCtrl` admite la visualización de archivos de distintos modos, como **iconos grandes**, **iconos pequeños**, **lista**, y **detalles**. Actualice la aplicación para implementar esta funcionalidad. Sugerencia: vea [ejemplos de Visual C++](../visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)  
