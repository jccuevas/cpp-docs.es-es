---
title: "Tutorial: Usar los nuevos controles de Shell de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles shell (MFC)"
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Usar los nuevos controles de Shell de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tutorial creará una aplicación similar al Explorador de archivos.  Creará una ventana que contendrá dos paneles.  El panel de la izquierda contendrá un objeto [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) que muestra el Escritorio en una vista jerárquica.  El panel de la derecha contendrá un objeto [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) que muestra los archivos de la carpeta seleccionada en el panel de la izquierda.  
  
## Requisitos previos  
 En este tutorial se supone que ha configurado [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para utilizar la **Configuración general de desarrollo**.  Si usa otra configuración de desarrollo, algunas ventanas de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] que utilizamos en este tutorial podrían no mostrarse de forma predeterminada.  
  
### Para crear una nueva aplicación MFC mediante el Asistente para aplicaciones MFC  
  
1.  Utilice el **Asistente para aplicaciones MFC** para crear una nueva aplicación MFC.  Para ejecutar el asistente, en el menú de **Archivo** seleccione **Nuevo** y, a continuación, seleccione **Proyecto**.  Aparecerá el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C\+\+** en el panel **Tipos de proyecto** y seleccione **MFC**.  A continuación, en el panel **Plantillas**, seleccione **Aplicación MFC**.  Escriba un nombre para el proyecto, por ejemplo, `MFCShellControls`, y haga clic en **Aceptar**.  Aparecerá el **Asistente para aplicaciones MFC**.  
  
3.  En el cuadro de diálogo **Asistente para aplicaciones MFC**, haga clic en **Siguiente**.  Aparecerá el panel **Tipo de aplicación**.  
  
4.  En el panel **Tipo de aplicación**, debajo de **Tipo de aplicación**, desactive la opción **Organización por fichas**.  A continuación, seleccione **Documento** y **Compatibilidad con la arquitectura documento\/vista**.  En **Estilo del proyecto**, seleccione **Visual Studio** y, en la lista desplegable **Estilo visual y colores**, seleccione **Office 2007 \(tema Azul\)**.  Deje el resto de las opciones tal como están.  Haga clic en **Siguiente** para mostrar el panel **Compatibilidad con documentos compuestos**.  
  
5.  En el panel **Compatibilidad con documentos compuestos**, seleccione **Ninguno**.  Haga clic en **Siguiente** para mostrar el panel **Cadenas de plantillas de doc.**  
  
6.  No realice ninguna modificación en el panel **Cadenas de plantillas de doc.** Haga clic en **Siguiente** para mostrar el panel **Compatibilidad con bases de datos**.  
  
7.  En el panel **Compatibilidad con bases de datos**, seleccione **Ninguno** porque esta aplicación no utiliza una base de datos.  Haga clic en **Siguiente** para mostrar el panel **Características de la interfaz de usuario**.  
  
8.  En el panel **Características de la interfaz de usuario**, compruebe que la opción **Usar una barra de menús y una barra de herramientas** está activada.  Deje el resto de las opciones tal como están.  Haga clic en **Siguiente** para mostrar el panel **Características avanzadas**.  
  
9. En el panel **Características avanzadas**, debajo de **Características avanzadas**, seleccione solo **Controles ActiveX** y **Manifiesto de controles comunes**.  Debajo de **Paneles de marco avanzados**, seleccione solo la opción **Panel de navegación**.  Esto hará que el asistente cree el panel a la izquierda de la ventana con un control `CMFCShellTreeCtrl` ya insertado.  Haga clic en **Siguiente** para mostrar el panel **Clases generadas**.  
  
10. No vamos a realizar cambios en el panel **Clases generadas**.  Por tanto, haga clic en **Finalizar** para crear el nuevo proyecto de MFC.  
  
11. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela.  Para compilar la aplicación, en el menú **Compilar**, seleccione **Compilar solución**.  Si la aplicación se compila correctamente, en el menú **Depurar**, seleccione **Iniciar depuración** para ejecutarla.  
  
     El asistente crea automáticamente una aplicación con una barra de menús estándar, una barra de herramientas estándar, una barra de estado estándar y una barra de Outlook a la izquierda de la ventana con una vista **Carpetas** y una vista **Calendario**.  
  
### Para agregar el control de lista de shell a la vista del documento  
  
1.  En esta sección, agregará una instancia de `CMFCShellListCtrl` a la vista que el asistente creó.  Haga doble clic en MFCShellControlsView.h en el **Explorador de soluciones** para abrir el archivo de encabezado de la vista.  
  
     Busque la directiva `#pragma once` cerca de la parte superior del archivo de encabezado.  Inmediatamente debajo de la directiva, agregue este código para incluir el archivo de encabezado para `CMFCShellListCtrl`:  
  
    ```  
    #include <afxShellListCtrl.h>  
    ```  
  
     Agregue una variable miembro de tipo `CMFCShellListCtrl`.  Primero, busque el siguiente comentario en el archivo de encabezado:  
  
    ```  
    // Generated message map functions  
    ```  
  
     Inmediatamente antes del comentario, agregue este código:  
  
    ```  
    private:  
        CMFCShellListCtrl m_wndList;  
    ```  
  
2.  El **Asistente para aplicaciones MFC** ya ha creado un objeto `CMFCShellTreeCtrl` en la clase `CMainFrame`, pero es miembro protegido.  Tendremos acceso a este objeto más adelante.  Por consiguiente, cree ahora un descriptor de acceso para él.  Haga doble clic en el **Explorador de soluciones** para abrir el archivo de encabezado MainFrm.h.  Localice el comentario siguiente:  
  
    ```  
    // Attributes  
    ```  
  
     Inmediatamente debajo de él, agregue la declaración de método siguiente:  
  
    ```  
    public:  
        CMFCShellTreeCtrl& GetShellTreeCtrl();  
    ```  
  
     A continuación, haga doble clic en el **Explorador de soluciones** para abrir el archivo de código fuente MainFrm.cpp.  En la parte inferior de ese archivo, agregue la definición de método siguiente:  
  
    ```  
    CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()  
    {  
        return m_wndTree;  
    }  
    ```  
  
3.  Ahora vamos a actualizar la clase `CMFCShellControlsView` para controlar el mensaje de Windows **WM\_CREATE**.  Abra el archivo de encabezado MFCShellControlsView.h y haga clic en esta línea de código:  
  
    ```  
    class CMFCShellControlsView : public CView  
    ```  
  
     A continuación, en la ventana **Propiedades**, haga clic en el icono **Mensajes**.  Desplácese hacia abajo hasta que encuentre el mensaje **WM\_CREATE**.  En la lista desplegable situada junto a **WM\_CREATE**, seleccione **\<Add\> OnCreate**.  De esta forma se crea un controlador de mensajes y se actualiza automáticamente el mapa de mensajes de MFC.  
  
     En el método `OnCreate` vamos a crear ahora nuestro propio objeto `CMFCShellListCtrl`.  Busque la definición del método de `OnCreate` en el archivo de código fuente MFCShellControlsView.cpp y reemplace la implementación por el código siguiente:  
  
    ```  
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
  
4.  Repita el paso anterior, esta vez para el mensaje **WM\_SIZE**.  Esto hará que la vista de las aplicaciones se rediseñe siempre que un usuario cambie el tamaño de la ventana de la aplicación.  Reemplace la definición del método `OnSize` por el código siguiente:  
  
    ```  
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)  
    {  
        CView::OnSize(nType, cx, cy);  
        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,  
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);  
    }  
    ```  
  
5.  El último paso es conectar los objetos `CMFCShellTreeCtrl` y `CMFCShellListCtrl` mediante el método [CMFCShellTreeCtrl::SetRelatedList](../Topic/CMFCShellTreeCtrl::SetRelatedList.md).  Después de llamar a este método, `CMFCShellListCtrl` mostrará automáticamente el contenido del elemento seleccionado en `CMFCShellTreeCtrl`.  Haremos esto en el método `OnActivateView`, que se invalida desde [CView::OnActivateView](../Topic/CView::OnActivateView.md).  
  
     En el archivo de encabezado MFCShellControlsView.h, dentro de la declaración de clase de `CMFCShellControlsView`, agregue la declaración de método siguiente:  
  
    ```  
    protected:  
        virtual void OnActivateView(BOOL bActivate,  
            CView* pActivateView,  
            CView* pDeactiveView);  
    ```  
  
     A continuación, agregue la definición de este método al archivo de código fuente MFCShellControlsView.cpp:  
  
    ```  
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,  
        CView* pActivateView,  
        CView* pDeactiveView)   
    {  
        if (bActivate && AfxGetMainWnd() != NULL)  
        {  
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);  
        }  
  
        CView::OnActivateView(bActivate, pActivateView, pDeactiveView);  
    }  
    ```  
  
     Dado que llamamos a los métodos desde la clase `CMainFrame`, debemos agregar una directiva `#include` en la parte superior del archivo de código fuente MFCShellControlsView.cpp:  
  
    ```  
    #include "MainFrm.h"  
    ```  
  
6.  Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela.  Para compilar la aplicación, en el menú **Compilar**, seleccione **Compilar solución**.  Si la aplicación se compila correctamente, en el menú **Depurar**, seleccione **Iniciar depuración** para ejecutarla.  
  
     Ahora deberían mostrarse los detalles del elemento seleccionado en el control `CMFCShellTreeCtrl` en el panel de vista.  Al hacer clic en un nodo en `CMFCShellTreeCtrl`, `CMFCShellListCtrl` se actualizará automáticamente.  Igualmente, si hace doble clic en una carpeta en `CMFCShellListCtrl`, `CMFCShellTreeCtrl` debe actualizarse automáticamente.  
  
     Haga clic con el botón secundario en cualquier elemento del control de árbol o del control de lista.  Observe que obtiene el mismo menú contextual que si utilizara el Explorador de archivos auténtico.  
  
## Pasos siguientes  
  
-   El asistente creó una barra de Outlook con un panel **Carpetas** y un panel **Calendario**.  Probablemente no tiene sentido colocar un panel **Calendario** en una ventana del Explorador.  Por consiguiente, vamos a quitarlo ahora.  
  
-   `CMFCShellListCtrl` admite la presentación de archivos de distintos modos, como **Iconos grandes**, **Iconos pequeños**, **Lista** y **Detalles**.  Actualice la aplicación para implementar esta funcionalidad.  Sugerencia: vea [Ejemplos de Visual C\+\+](../top/visual-cpp-samples.md).  
  
## Vea también  
 [Tutoriales](../mfc/walkthroughs-mfc.md)