---
title: "TN041: Migraci&#243;n de MFC/OLE1 a MFC/OLE 2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "convertir OLE1 a OLE2"
  - "migrar OLE1 a OLE2"
  - "migración [C++], OLE1 to OLE2"
  - "OLE1 [C++]"
  - "OLE2 [C++]"
  - "trasladar OLE1 a OLE2"
  - "TN041"
  - "actualizar aplicaciones de Visual C++, OLE1 to OLE2"
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN041: Migraci&#243;n de MFC/OLE1 a MFC/OLE 2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
## Problemas generales relacionados con la migración  
 Uno de los objetivos de diseño para OLE 2 clases de MFC 2,5 \(y más alto\) era conservar gran parte de la misma arquitectura establecida en MFC 2,0 para compatibilidad OLE 1,0.  Como resultado, muchas de las mismas clases VIEJAS en MFC 2,0 permanecen en esta versión de MFC \(`COleDocument`, `COleServerDoc`, `COleClientItem`, `COleServerItem`\).  Además, muchos de API de estas clases son exactamente iguales.  Sin embargo, OLE 2 es drásticamente diferente OLE 1,0 por lo que puede esperar que los detalles cambien.  Si está familiarizado con la compatibilidad de MFC 2.0 ' s OLE1, se sentirá en casa con compatibilidad con MFC 2,0.  
  
 Si está tomando una aplicación existente MFC\/OLE1 y está agregando funcionalidad OLE 2 a él, debe leer esta nota primero.  Esta nota trata algunos problemas generales que puede encontrar a portal la funcionalidad OLE1 a MFC\/OLE 2 y a continuación se describen los problemas destapados mientras portal dos aplicaciones incluidas en MFC 2,0: los ejemplos [OCLIENT](../top/visual-cpp-samples.md) y [HIERSVR](../top/visual-cpp-samples.md)MFC OLE.  
  
## El documento de MFC y la arquitectura de la vista es importantes  
 Si la aplicación no utiliza la arquitectura documento\/vista de MFC y desea agregar compatibilidad OLE 2 a la aplicación, es la hora de desplazarse al documento\/a la vista.  Realizan muchas de las ventajas de OLE de MFC 2 clases solo una vez que la aplicación utiliza la arquitectura y los componentes integrados de MFC.  
  
 Implementar un servidor o un contenedor sin utilizar la arquitectura de MFC es posible, pero no se recomienda.  
  
## Implementación de MFC de uso en lugar de ser  
 Las clases “implementación conservará” de MFC como `CToolBar`, `CStatusBar`, y `CScrollView` tienen código integrado de caso especial para compatibilidad OLE 2.  Por lo tanto, si puede utilizar estas clases en la aplicación se beneficiará de esfuerzo título en ellas para crear les OLE monitores.  Una vez más es posible a “enrollamiento\-\-propias” clases aquí para estos propósitos, pero no se sugiere.  Si necesita implementar funcionalidad similar, el código fuente de MFC es una referencia excelente para tratar de algunos de los puntos más precisión OLE \(sobre todo cuando se trata de activación in situ\).  
  
## Examine el código de ejemplo de MFC  
 Hay varios ejemplos de MFC que incluyen funcionalidad OLE.  Cada una de estas aplicaciones implementa OLE de otro ángulo:  
  
-   [HIERSVR](../top/visual-cpp-samples.md) significaba principalmente para su uso como una aplicación de servidor.  Incluida en MFC 2,0 como aplicación MFC\/OLE1 y se ha portado a MFC\/OLE 2 y después extendidas tales que implementa muchas características de OLE disponibles en OLE 2.  
  
-   [OCLIENT](../top/visual-cpp-samples.md) Esta es una aplicación contenedora independiente, lo que sucede para mostrar muchas de las características de OLE de un punto de vista del contenedor.  Se ha trasladado también MFC 2,0 y, a continuación mejorada para admitir muchas de las características más avanzadas de OLE, como formatos personalizados del portapapeles y vínculos a los elementos incrustados.  
  
-   la aplicación de[DRAWCLI](../top/visual-cpp-samples.md)This implementa compatibilidad OLE de contenedor como OCLIENT hace, excepto en que lo hace en el marco de programa de dibujo orientado existente.  Muestra cómo puede implementar compatibilidad OLE de contenedor y se integran en la aplicación existente.  
  
-   la aplicación de[SUPERPAD](../top/visual-cpp-samples.md)This, así como una aplicación independiente adecuada, también es servidor OLE.  Compatibilidad de servidor que implementa es muy minimalista.  De especial interés es cómo utiliza servicios de portapapeles OLE para copiar datos en el portapapeles, pero usa la funcionalidad incorporada en el control de “editar” de Windows para implementar la funcionalidad de pegar desde el portapapeles.  Esto muestra una combinación interesante de uso así como de integración tradicionales de la API de Windows con el nuevo API OLE.  
  
 Para obtener más información sobre las aplicaciones de ejemplo, vea la Ayuda de ejemplo de MFC”.  
  
## Caso práctico: OCLIENT MFC 2,0  
 Tal y como se describe anteriormente, [OCLIENT](../top/visual-cpp-samples.md) se incluyó en MFC 2,0 e implementó OLE con MFC\/OLE1.  Los pasos para los que esta aplicación se convierte inicialmente para utilizar las clases de MFC\/OLE 2 se describen a continuación.  Varias características se agregaron después de que el puerto inicial completada para mostrar mejor las clases de MFC\/OLE.  Estas características no se abordan aquí; consulte el ejemplo propio para obtener más información sobre estas características avanzadas.  
  
> [!NOTE]
>  Los errores del compilador y el proceso paso a paso creados con Visual C\+\+ 2.0.  Los mensajes de error y las ubicaciones específicos pueden haber cambiado con Visual C\+\+ 4,0, pero la información conceptual sigue siendo válida.  
  
## La en ejecución  
 El enfoque llevar el puerto el ejemplo OCLIENT a MFC\/OLE es iniciar el y corregir los errores obvios de compilador destinada a.  Si se tome el ejemplo OCLIENT MFC 2,0 y se compila en esta versión de MFC, descubrirá que no hay que muchos errores a resolver.  Los errores en el orden en que se produjeron se describen a continuación.  
  
## Errores de compilación y de la corrección  
  
```  
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters  
```  
  
 El primer error se hace referencia a `COleClientItem::Draw`.  En MFC\/OLE1 tardó más parámetros que la versión de MFC\/OLE toma.  Los parámetros adicionales no estaban a menudo necesarios y normalmente NULL \(como en este ejemplo\).  Esta versión de MFC puede determinar automáticamente los valores de los lpWBounds cuando la CDC a la que se dibuja es un metarchivo DC.  Además, el parámetro de pFormatDC ya no es necesario porque el marco compilará uno de “TITLE. de atributo” de pDC pasado.  Para corregir en este problema, quite simplemente los dos parámetros NULL adicionales a la llamada de dibujo.  
  
```  
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier  
\oclient\mainview.cpp(273) : error C2057: expected constant expression  
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
```  
  
 Los errores sobre resultado el hecho de que todo el **COleClientItem::CreateXXXX** funcione en MFC\/OLE1 necesarias que un nombre único se dedica para representar el elemento.  Éste es un requisito de API OLE subyacente.  Esto no es necesario en MFC\/OLE 2 como OLE 2 no utiliza DDE como el mecanismo subyacente de comunicaciones \(el nombre utilizado en conversaciones DDE\).  Para corregir este problema, puede quitar la función de **CreateNewName** junto con todas las referencias a ella.  Es fácil averiguar qué cada función de MFC\/OLE está esperando esta versión simplemente colocando el cursor en la llamada y presionando F1.  
  
 Otra área que difiere significativamente es el control del portapapeles OLE 2.  Con OLE1, utilizó el portapapeles las API de Windows interactúa con el portapapeles.  Con OLE 2 esto se hace con un mecanismo diferente.  El MFC\/OLE1 API suponía que el portapapeles estaba abierta antes de copiar un objeto de `COleClientItem` en el portapapeles.  Esto no es necesario y hace que todas las operaciones del portapapeles de MFC\/OLE el error.  Mientras edita el código para quitar las dependencias de **CreateNewName**, también debe quitar el código que abre y cierra el portapapeles de Windows.  
  
```  
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier  
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function  
\oclient\mainview.cpp(344) : error C2057: expected constant expression  
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'  
```  
  
 Resultado de estos errores de controlador de **CMainView::OnInsertObject** .  Administrar “el comando de objeto New INSERT” es otra área donde las cosas han cambiado muy un bit.  En este caso, es más fácil combinar simplemente la implementación original que proporcionada por AppWizard para una nueva aplicación contenedora OLE.  De hecho, es una técnica que se puede aplicar a trasladar otras aplicaciones.  En MFC\/OLE1, mostró “el diálogo de objeto INSERT” llamando a la función de **AfxOleInsertDialog** .  En esta versión se crea un objeto del diálogo de **COleInsertObject** y llama a `DoModal`.  Además, los nuevos elementos de OLE se crean con **CLSID** en lugar de una cadena de classname.  El resultado final debe tener la siguiente apariencia  
  
```  
COleInsertDialog dlg;  
if (dlg.DoModal() != IDOK)  
    return;  
  
BeginWaitCursor();  
  
CRectItem* pItem = NULL;  
TRY  
{  
    // First create the C++ object  
    pItem = GetDocument()->CreateItem();  
    ASSERT_VALID(pItem);  
  
    // Initialize the item from the dialog data.  
    if (!dlg.CreateItem(pItem))  
        AfxThrowMemoryException();  
           // any exception will do  
    ASSERT_VALID(pItem);  
  
    // run the object if appropriate  
    if (dlg.GetSelectionType() ==   
            COleInsertDialog::createNewItem)  
        pItem->DoVerb(OLEIVERB_SHOW, this);  
  
    // update right away  
    pItem->UpdateLink();  
    pItem->UpdateItemRectFromServer();  
  
    // set selection to newly inserted item  
    SetSelection(pItem);  
    pItem->Invalidate();  
}  
CATCH (CException, e)  
{    
    // clean up item  
    if (pItem != NULL)  
        GetDocument()->DeleteItem(pItem);  
  
    AfxMessageBox(IDP_FAILED_TO_CREATE);  
}  
END_CATCH  
  
EndWaitCursor();  
```  
  
> [!NOTE]
>  El objeto New INSERT puede ser diferente de la aplicación\):  
  
 También es necesario incluir \<afxodlgs.h, que\>contiene la declaración de la clase de diálogo de **COleInsertObject** junto con los otros cuadros de diálogo estándar proporcionados por MFC.  
  
```  
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier  
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters  
```  
  
 Estos errores se producen por el hecho de que las constantes algún OLE1 han cambiado en OLE 2, aunque en concepto son iguales.  En este caso **OLEVERB\_PRIMARY** ha cambiado a `OLEIVERB_PRIMARY`.  En OLE1 y OLE 2, el verbo primario ejecutan normalmente mediante un contenedor cuando el usuario hace doble clic en un elemento.  
  
 Además, `DoVerb` ahora toma un parámetro adicional \(un puntero a una vista \(`CView`\*\).  Este parámetro solo se utiliza para implementar la “edición de Visual” \(o activación in situ\).  De momento establece ese parámetro en NULL, porque no está implementando esta característica en este momento.  
  
 Para asegurarse de que el marco nunca intente a en contexto active, debe invalidar `COleClientItem::CanActivate` como sigue:  
  
```  
BOOL CRectItem::CanActivate()  
{  
    return FALSE;  
}  
  
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier  
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function  
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier  
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function  
```  
  
 En MFC\/OLE1, **COleClientItem::GetBounds** y **SetBounds** utilizados para ver y manipular la extensión de un elemento \(los miembros de **left** y de **arriba** eran siempre cero\).  En MFC\/OLE 2 es compatible más directamente por `COleClientItem::GetExtent` y `SetExtent`, que tratan de **TAMAÑO** o de `CSize` en su lugar.  
  
 El código para el nuevo SetItemRectToServer, y las llamadas de UpdateItemRectFromServer con esta apariencia:  
  
```  
BOOL CRectItem::UpdateItemRectFromServer()  
{  
   ASSERT(m_bTrackServerSize);  
   CSize size;  
   if (!GetExtent(&size))  
      return FALSE;    // blank  
  
   // map from HIMETRIC to screen coordinates  
   {  
      CClientDC screenDC(NULL);  
      screenDC.SetMapMode(MM_HIMETRIC);  
      screenDC.LPtoDP(&size);  
   }  
   // just set the item size  
   if (m_rect.Size() != size)  
   {  
      // invalidate the old size/position  
      Invalidate();  
      m_rect.right = m_rect.left + size.cx;  
      m_rect.bottom = m_rect.top + size.cy;  
      // as well as the new size/position  
      Invalidate();  
   }  
   return TRUE;  
}  
  
BOOL CRectItem::SetItemRectToServer()  
{  
   // set the official bounds for the embedded item  
   CSize size = m_rect.Size();  
   {  
      CClientDC screenDC(NULL);  
      screenDC.SetMapMode(MM_HIMETRIC);  
      screenDC.DPtoLP(&size);  
   }  
   TRY  
   {  
      SetExtent(size);  // may do a wait  
   }  
   CATCH(CException, e)  
   {  
      return FALSE;  // links will not allow SetBounds  
   }  
   END_CATCH  
   return TRUE;  
}  
  
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'  
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier  
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function  
```  
  
 En las llamadas API sincrónicas MFC\/OLE1 de un contenedor a un servidor *se simulados*, porque OLE1 era inherentemente asincrónico en muchos casos.  Era necesario comprobar una llamada asincrónica pendiente en curso antes de procesar los comandos de usuario.  MFC\/OLE1 proporcionado a la función de **COleClientItem::InWaitForRelease** para ello.  En MFC\/OLE 2 no es necesario, por lo que puede quitar la invalidación de OnCommand en CMainFrame todos juntos.  
  
 En este punto OCLIENT compilará y vincular.  
  
## Otros cambios necesarios  
 Hay pocas cosas que no se hace que conservará OCLIENT run, sin embargo.  Es mejor ahora solucionar estos problemas en lugar de más adelante.  
  
 En primer lugar, es necesario inicializar las bibliotecas VIEJAS.  Esto se hace llamando a **AfxOleInit** de `InitInstance`:  
  
```  
if (!AfxOleInit())  
{  
  AfxMessageBox("Failed to initialize OLE libraries");  
  return FALSE;  
}  
```  
  
 También es conveniente comprobar si hay funciones virtuales para los cambios de la lista de parámetros.  Una por función es `COleClientItem::OnChange`, invalide en cada aplicación contenedora de MFC\/OLE.  Examinando la ayuda en línea, verá que un “dwParam adicional de DWORD” se agregó.  El nuevo CRectItem::OnChange tiene la apariencia siguiente:  
  
```  
void   
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)  
{  
  if (m_bTrackServerSize &&  
        !UpdateItemRectFromServer())  
  {  
    // Blank object  
    if (wNotification == OLE_CLOSED)  
    {  
      // no data received for the object - destroy it  
      ASSERT(!IsVisible());  
      GetDocument()->DeleteItem(this);  
      return;   // no update (item is gone now)  
    }  
  }  
  if (wNotification != OLE_CLOSED)  
      Dirty();  
  Invalidate();  // any change will cause a redraw  
}  
```  
  
 En MFC\/OLE1, las aplicaciones contenedoras derivadas la clase document de **COleClientDoc**.  En MFC\/OLE 2 esta clase se ha quitado y reemplaza por `COleDocument` \(esta nueva organización facilita compilar el contenedor o aplicaciones de servidor\).  Hay `#define` que asigna **COleClientDoc** a `COleDocument` para simplificar la portabilidad de las aplicaciones MFC\/OLE1 a MFC\/OLE 2, como OCLIENT.  Una de las características no proporcionadas por `COleDocument` proporcionados por **COleClientDoc** es las entradas estándar del mapa de mensajes del comando.  Se hace esto para que las aplicaciones de servidor, que también usan `COleDocument` \(indirectamente\), no tomen con ellas la sobrecarga de estos controladores de comandos a menos que sean un contenedor o una aplicación de servidor.  Necesita agregar las entradas siguientes al mensaje de CMainDoc asignado:  
  
```  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)  
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)  
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)  
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)  
```  
  
 La implementación de todos estos comandos está en `COleDocument`, que es la clase base para el documento.  
  
 En este punto, OCLIENT es una aplicación contenedora OLE funcional.  Es posible insertar elementos de cualquier tipo \(OLE1 o OLE 2\).  Puesto que el código necesario para habilitar la activación en contexto no se implementa, los elementos se editan en una ventana independiente como con OLE1.  La siguiente sección describe los cambios necesarios en la edición en contexto habilitada \(a veces denominada “edición de Visual”\).  
  
## Agregando la “edición visual”  
 Una de las características más interesantes OLE es activación en contexto \(o “edición de Visual”\).  Esta característica permite la aplicación de servidor adopte el control partes de la interfaz de usuario del contenedor proporciona una interfaz más sin problemas de edición para el usuario.  Para implementar la activación en contexto a OCLIENT, algunos recursos especiales deben agregarse, junto con algún código adicional.  AppWizard proporcionan estos recursos y el código normalmente \(de hecho, gran parte del código mostrado se orden prestado directamente de una nueva aplicación de AppWizard con el “contenedor”.  
  
 En primer lugar, es necesario agregar un recurso de menú que se utilizará cuando hay un elemento que está activo en contexto.  Puede crear este recurso adicional en el menú en Visual C\+\+ copiando el recurso de IDR\_OCLITYPE y quitar todos menos el archivo y la ventana estallido\- UPS.  Dos barras separadoras se insertan entre el archivo y la ventana estallido\- UPS para indicar la separación de grupos \(debe ser similar a: archivo &#124; &#124; Ventana\).  Para obtener más información sobre qué considera medio de estos separadores y cómo se combinan los menús de servidor y el contenedor “menús y recursos: Menú Combinación” en *OLE 2 clases*.  
  
 Una vez hecho estos menús crear, debe dejar el marco saber sobre ellos.  Esto se hace llamando a `CDocTemplate::SetContainerInfo` de plantilla de documento antes de que se agregue a la plantilla de documento mostrada en el InitInstance.  El nuevo código para registrar la plantilla de documento tiene el siguiente aspecto:  
  
```  
CDocTemplate* pTemplate = new CMultiDocTemplate(  
    IDR_OLECLITYPE,  
    RUNTIME_CLASS(CMainDoc),  
    RUNTIME_CLASS(CMDIChildWnd),    // standard MDI child frame  
    RUNTIME_CLASS(CMainView));  
pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);  
AddDocTemplate(pTemplate);  
```  
  
 El recurso de IDR\_OLECLITYPE\_INPLACE es el recurso en contexto especial creado en Visual C\+\+.  
  
 Para habilitar la activación en contexto, hay algunos aspectos que necesitan cambiar en la clase derivada junto con la clase derivada de `COleClientItem` \(CRectItem\) de `CView` \(CMainView\).  Todas estas reemplazan proporcionan AppWizard y la mayor parte de la implementación vendrá directamente de una aplicación predeterminada de AppWizard.  
  
 En el primer paso de este puerto, la activación en contexto se deshabilita completamente reemplazando `COleClientItem::CanActivate`.  Esta invalidación debe quitarse para permitir la activación en contexto.  Además, NULL se pasó a todas las llamadas a `DoVerb` \(hay dos de ellas\) porque proporcionar a la vista sólo fue necesario para la activación en contexto.  Para implementar los activación in situ, es necesario pasar la vista correcta en la llamada de `DoVerb` .  Una de estas llamadas está en **CMainView::OnInsertObject**:  
  
```  
pItem->DoVerb(OLEIVERB_SHOW, this);  
```  
  
 Otro está en **CMainView::OnLButtonDblClk**:  
  
```  
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);  
```  
  
 Es necesario reemplazar `COleClientItem::OnGetItemPosition`.  Esto indica al servidor donde colocar la ventana en relación con la ventana contenedora cuando el elemento está en contexto elevado.  Para OCLIENT, la implementación es trivial:  
  
```  
void CRectItem::OnGetItemPosition(CRect& rPosition)  
{  
    rPosition = m_rect;  
}  
```  
  
 La mayoría de los servidores también implementan lo que se denomina “cambiar el tamaño en contexto”. Esto permite que mover la ventana de servidor es ordenada y mientras el usuario editando el elemento.  El contenedor debería participar en esta acción, como mover o cambiar el tamaño de la ventana determina normalmente a la posición y el tamaño en el documento contenedor.  La implementación de OCLIENT sincroniza el rectángulo interno mantenido por el m\_rect con la nueva posición y tamaño.  
  
```  
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)  
{  
    ASSERT_VALID(this);  
  
    if (!COleClientItem::OnChangeItemPosition(rectPos))  
        return FALSE;  
  
    Invalidate();  
    m_rect = rectPos;  
    Invalidate();  
    GetDocument()->SetModifiedFlag();  
  
    return TRUE;  
}  
```  
  
 En este punto, hay suficiente código para permitir un elemento sea haber producido en contexto y trate de tamaño y de mover el elemento cuando está activo, pero ningún código permitirá que el usuario salga de la sesión de edición.  Aunque algunos servidores proporcionan esta funcionalidad propios controlando la clave de escape, se sugiere que los contenedores proporcionan dos maneras de desactivar un elemento: \(1\) haciendo clic fuera del elemento y \(2\), presione la tecla ESC.  
  
 Para la tecla ESC, agregue un acelerador con Visual C\+\+ que asigna la clave VK\_ESCAPE a un comando, ID\_CANCEL\_EDIT se agrega a los recursos.  El controlador para este comando siguiente:  
  
```  
// The following command handler provides the standard  
// keyboard user interface to cancel an in-place  
// editing session.void CMainView::OnCancelEdit()  
{  
    // Close any in-place active item on this view.  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL)  
        pActiveItem->Close();  
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);  
}  
```  
  
 Para controlar el caso en que el usuario haga clic fuera del elemento, agregue el código siguiente al inicio de **CMainView::SetSelection**:  
  
```  
if (pNewSel != m_pSelection || pNewSel == NULL)  
{  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL && pActiveItem != pNewSel)  
        pActiveItem->Close();  
}  
  
```  
  
 Cuando un elemento está activo en contexto, debe tener el foco.  Para asegurarse de esto es el caso que administra OnSetFocus para transferir el foco siempre el elemento activo cuando la vista recibe el foco:  
  
```  
// Special handling of OnSetFocus and OnSize are required   
// when an object is being edited in-place.  
void CMainView::OnSetFocus(CWnd* pOldWnd)  
{  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL &&  
    pActiveItem->GetItemState() == COleClientItem::activeUIState)  
    {  
        // need to set focus to this item if it is same view  
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();  
        if (pWnd != NULL)  
        {  
            pWnd->SetFocus();  // don't call the base class  
            return;  
        }  
    }  
  
    CView::OnSetFocus(pOldWnd);  
}  
```  
  
 Cuando se cambia el tamaño de la vista, se debe notificar el elemento activo que el rectángulo de recorte ha cambiado.  Para ello se proporciona un controlador para `OnSize`:  
  
```  
void CMainView::OnSize(UINT nType, int cx, int cy)  
{  
    CView::OnSize(nType, cx, cy);  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL)  
        pActiveItem->SetItemRects();  
}  
```  
  
## Caso práctico: HIERSVR MFC 2,0  
 [HIERSVR](../top/visual-cpp-samples.md) también se incluye en MFC 2,0 e implementó OLE con MFC\/OLE1.  Esta nota describe brevemente los pasos en que esta aplicación se convierte inicialmente para utilizar las clases de MFC\/OLE 2.  Varias características se agregaron después de que el puerto inicial completada para mostrar mejor las clases de MFC\/OLE 2.  Estas características no se abordan aquí; consulte el ejemplo propio para obtener más información sobre estas características avanzadas.  
  
> [!NOTE]
>  Los errores del compilador y el proceso paso a paso creados con Visual C\+\+ 2.0.  Los mensajes de error y las ubicaciones específicos pueden haber cambiado con Visual C\+\+ 4,0, pero la información conceptual sigue siendo válida.  
  
## La en ejecución  
 El enfoque llevar el puerto el ejemplo HIERSVR a MFC\/OLE es iniciar el y corregir los errores obvios de compilador destinada a.  Si se tome el ejemplo HIERSVR MFC 2,0 y se compila en esta versión de MFC, descubrirá que no hay muchos errores a resolver \(aunque hay más que con el ejemplo OCLIENT\).  Los errores en el orden en que aparecen normalmente se describen a continuación.  
  
## Errores de compilación y de la corrección  
  
```  
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'  
```  
  
 Este primer error indica un problema mucho mayor con la función de `InitInstance` para los servidores.  La inicialización necesaria para un servidor OLE probablemente uno de los cambios mayores que tendrá que realizar en la aplicación MFC\/OLE1 para obtenerlo en ejecución.  La mejor aspecto que hacer es examinar lo que crea AppWizard para un servidor OLE y modifica el código según corresponda.  A continuación se muestran algunos puntos a tener en cuenta:  
  
 Es necesario inicializar las bibliotecas VIEJAS llamando a **AfxOleInit**  
  
 Llamada SetServerInfo en el objeto de plantilla de documento a identificadores determinados de recursos de servidor y la información de la clase en tiempo de ejecución que no se puede establecer con el constructor de `CDocTemplate` .  
  
 No muestre la ventana principal de la aplicación si \/Embedding está presente en la línea de comandos.  
  
 Necesitará **GUID** para el documento.  Esto es un identificador único para el tipo de documento \(128 bits\).  AppWizard creará uno para se — tan si utiliza la técnica descrita aquí para copiar el nuevo código de una aplicación de servidor generada AppWizard, puede “robar simplemente” GUID de esa aplicación.  Si no, puede usar la utilidad de GUIDGEN.EXE en el directorio BIN.  
  
 Es necesario “conectar” el objeto de `COleTemplateServer` a la plantilla de documento llamando a `COleTemplateServer::ConnectTemplate`.  
  
 Actualice el sistema cuando la aplicación es independiente ejecutado.  Así, si el usuario mueve el .EXE para la aplicación, la elevación de su nueva ubicación actualizará la base de datos de registro del sistema de Windows para que apunte a la nueva ubicación.  
  
 Después de aplicar todos estos cambios según lo que crea AppWizard para `InitInstance`, `InitInstance` \(y GUID relacionado\) para HIERSVR debe leer como sigue:  
  
```  
// this is the GUID for HIERSVR documents  
static const GUID BASED_CODE clsid =  
    { 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };  
  
/////////////////////////////////////////////////////////////////////////////  
// COLEServerApp initialization  
  
BOOL COLEServerApp::InitInstance()  
{  
    // OLE 2 initialization  
    if (!AfxOleInit())  
    {  
        AfxMessageBox("Initialization of the OLE failed!");  
        return FALSE;  
    }  
  
    // Standard initialization  
    LoadStdProfileSettings(); // Load standard INI file options   
  
    // Register document templates  
    CDocTemplate* pDocTemplate;  
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,  
        RUNTIME_CLASS(CServerDoc),     
        RUNTIME_CLASS(CMDIChildWnd),  
        RUNTIME_CLASS(CServerView));  
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);  
    AddDocTemplate(pDocTemplate);  
  
    // create main MDI Frame window  
    CMainFrame* pMainFrame = new CMainFrame;  
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))  
        return FALSE;  
    m_pMainWnd = pMainFrame;  
  
    SetDialogBkColor();   // gray look  
  
    // enable file manager drag/drop and DDE Execute open  
    m_pMainWnd->DragAcceptFiles();  
    EnableShellOpen();  
  
    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);  
    COleTemplateServer::RegisterAll();  
  
    // try to launch as an OLE server  
    if (RunEmbedded())  
    {  
        // "short-circuit" initialization -- run as server!  
        return TRUE;  
    }  
    m_server.UpdateRegistry();  
    RegisterShellFileTypes();  
  
    // not run as OLE server, so show the main window  
    if (m_lpCmdLine[0] == '\0')  
    {  
        // create a new (empty) document  
        OnFileNew();  
    }  
    else  
    {  
        // open an existing document  
        OpenDocumentFile(m_lpCmdLine);  
    }  
  
    pMainFrame->ShowWindow(m_nCmdShow);  
    pMainFrame->UpdateWindow();  
  
    return TRUE;  
}  
```  
  
 Observará que el código anterior hace referencia a un nuevo Id. de recurso, IDR\_HIERSVRTYPE\_SRVR\_EMB.  Éste es el recurso de menú que se utilizará cuando se edita un documento incrustado en otro contenedor.  En MFC\/OLE1 los elementos de menú específicos de editar un elemento incrustado se modificaron simultáneamente.  Utilizando una estructura de menú totalmente diferente al editar un elemento incrustado en lugar de editar un documento basado en archivos facilita proporcionar diferentes interfaces de usuario para estos dos modos independientes.  Como verá más adelante, utilice un recurso completamente independiente de menú al editar un objeto incrustado en contexto.  
  
 Para crear este recurso, cargue el script de recursos en Visual C\+\+ y copie el recurso existente del menú de IDR\_HIERSVRTYPE.  Cambie el nombre del nuevo recurso a IDR\_HIERSVRTYPE\_SRVR\_EMB \(es la misma convención de nomenclatura que AppWizard utiliza\).  El cambio siguiente “archivo Guardar” a “archivo actualiza”; dele el identificador **ID\_FILE\_UPDATE**de comando.  También cambie el “archivo Guardar como” “a la copia para guardar archivos como”; dele el identificador **ID\_FILE\_SAVE\_COPY\_AS**de comando.  El marco de trabajo proporciona la implementación de los comandos.  
  
```  
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations  
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers  
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'  
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'  
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers  
```  
  
 Hay varios errores resultando de reemplazo de `OnSetData`, ya que está haciendo referencia al tipo de **OLESTATUS** .  **OLESTATUS** era los errores devueltos OLE1 de la forma.  Esto ha cambiado a `HRESULT` en OLE 2, aunque MFC convierte normalmente `HRESULT` en `COleException` que contiene el error.  En este caso concreto, el reemplazo de `OnSetData` ya no es necesaria, lo que lo más sencillo es quitarlo.  
  
```  
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters  
```  
  
 El constructor de `COleServerItem` toma un parámetro extensor “BOOL”.  Este marcador determina cómo haga a la administración de memoria en los objetos de `COleServerItem` .  Estableciéndolo en TRUE, el marco controla la administración de memoria de estos objetos — eliminarlos cuando ya no son necesarios.  HIERSVR usa objetos de **CServerItem** \(derivado de `COleServerItem`\) como parte de los datos nativos, de modo que se establezca esta marca en FALSE.  Esto permite HIERSVR determinar cuándo se elimina cada elemento del servidor.  
  
```  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
```  
  
 Cuando estos errores indica, hay algunas funciones “puro\- virtuales” que no han sido reemplazadas en CServerItem.  Lo más probable es que se por el hecho de que la lista de parámetros de OnDraw ha cambiado.  Para corregir este error, cambie **CServerItem::OnDraw** como sigue \(así como la declaración en svritem.h\):  
  
```  
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)  
{  
    // request from OLE to draw node  
    pDC->SetMapMode(MM_TEXT); // always in pixels  
    return DoDraw(pDC, CPoint(0,0), FALSE);  
}  
```  
  
 El nuevo parámetro es “rSize”.  Esto permite completar el tamaño del gráfico, si es apropiado.  Este tamaño debe estar en **HIMETRIC**.  En este caso, no es conveniente completar este valor, lo que el marco de trabajo llama a `OnGetExtent` para recuperar la extensión.  Para que funcione, tendrá que implementar `OnGetExtent`:  
  
```  
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)  
{  
    if (dwDrawAspect != DVASPECT_CONTENT)  
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);  
  
    rSize = CalcNodeSize();  
    return TRUE;  
}  
  
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier  
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type  
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,int )__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'  
```  
  
 En función de CServerItem::CalcNodeSize el tamaño del elemento se convierte en **HIMETRIC** y almacenado en **m\_rectBounds**.  El miembro indocumentado de '**m\_rectBounds**' de `COleServerItem` no existe \(ha reemplazado parcialmente por `m_sizeExtent`, pero en OLE 2 este miembro tiene un uso ligeramente diferente que **m\_rectBounds** hizo en OLE1\).  En lugar de establecer el tamaño de **HIMETRIC** en esta variable miembro, se devolverá.  Este valor devuelto se utiliza en `OnGetExtent`, implementado previamente.  
  
```  
CSize CServerItem::CalcNodeSize()  
{  
    CClientDC dcScreen(NULL);  
  
    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,  
      m_strDescription.GetLength());  
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);  
  
    // set suggested HIMETRIC size  
    CSize size(m_sizeNode.cx, m_sizeNode.cy);  
    dcScreen.SetMapMode(MM_HIMETRIC);  
    dcScreen.DPtoLP(&size);  
    return size;  
}  
```  
  
 CServerItem también invalida **COleServerItem::OnGetTextData**.  Esta función está obsoleto en MFC\/OLE y se sustituye por un mecanismo diferente.  La versión de MFC 3,0 de ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md) MFC implementa esta funcionalidad reemplazando `COleServerItem::OnRenderFileData`.  Esta funcionalidad no es importante para este puerto básico, por lo que puede quitar la invalidación de OnGetTextData.  
  
 Hay muchos más errores en svritem.cpp que no se han dirigido.  No son errores “reales” — simplemente errores producidos por errores anteriores.  
  
```  
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters  
```  
  
 `COleServerItem::CopyToClipboard` ya no admite el marcador “bIncludeNative”.  Los datos nativos \(los datos guardados en escrito por la función Serialize del elemento del servidor\) siempre se copia, por lo que quita el primer parámetro.  Además, `CopyToClipboard` produce una excepción cuando un error ocurre en lugar de devolver FALSE.  Cambie el código para CServerView::OnEditCopy como sigue:  
  
```  
void CServerView::OnEditCopy()  
{  
    if (m_pSelectedNode == NULL)  
        AfxThrowNotSupportedException();  
  
    TRY  
    {  
        m_pSelectedNode->CopyToClipboard(TRUE);  
    }  
    CATCH_ALL(e)  
    {  
        AfxMessageBox("Copy to clipboard failed");  
    }  
    END_CATCH_ALL     
}  
```  
  
 Aunque hubiera más errores provocados por la compilación de la versión de MFC 2,0 HIERSVR que había para la misma versión de OCLIENT, había realmente menos cambios.  
  
 En este punto HIERSVR compilará y vincular y funciona como un servidor OLE, pero sin la característica de la edición en contexto, que se implementará después.  
  
## Agregando la “edición visual”  
 Para agregar la “edición de Visual” \(o activación in situ\) en esta aplicación de servidor, sólo hay algunos aspectos que debe tener cuidado de:  
  
-   Necesita un recurso especial de menú utilizar cuando el elemento está activo en contexto.  
  
-   Esta aplicación incluye una barra de herramientas, por lo que deberá una barra de herramientas con solo un subconjunto de la barra de herramientas normal coincidir con los comandos de menú disponibles del servidor \(coincide con el recurso de menú mencionado anteriormente\).  
  
-   Necesita una nueva clase derivada de `COleIPFrameWnd` que proporciona la interfaz de usuario en contexto \(como CMainFrame, derivado de `CMDIFrameWnd`, proporciona la interfaz de usuario de MDI\).  
  
-   Debe hablar el marco de estos recursos y clases especiales.  
  
 El recurso de menú es fácil crear.  Ejecute Visual C\+\+, copie el recurso IDR\_HIERSVRTYPE de menú a un recurso de menú denominado IDR\_HIERSVRTYPE\_SRVR\_IP.  Modifique el menú para dejar los menús emergentes sólo de edición y del menú ayuda.  Agregue dos separadores el menú entre la edición y menús de ayuda \(debe ser similar a: edición &#124; &#124; Ayuda\).  Para obtener más información sobre qué medio de estos separadores y cómo se combinan los menús de servidor y el contenedor, vea “menús y recursos: Menú Combinación” en *OLE 2 clases*.  
  
 El mapa de bits para la barra de herramientas del subconjunto fácil crear copiando el de una nueva aplicación para AppWizard con una opción de “Servidor” activada.  Este mapa de bits se puede importar después en Visual C\+\+.  Asegúrese de asignar al mapa de bits un identificador de IDR\_HIERSVRTYPE\_SRVR\_IP.  
  
 La clase derivada de `COleIPFrameWnd` se puede copiar de una aplicación para AppWizard con el servidor también.  Copie los dos archivos, IPFRAME.CPP e IPFRAME.H y agréguela al proyecto.  Asegúrese de que la llamada de `LoadBitmap` hace referencia a IDR\_HIERSVRTYPE\_SRVR\_IP, el mapa de bits creado en el paso anterior.  
  
 Ahora que crean a todos los nuevos recursos y clases, agregue el código necesario para que el marco sepa sobre éstos \(y sabe que esta aplicación admite la edición en contexto\).  Esto se hace agregando más parámetros a la llamada de `SetServerInfo` en función de `InitInstance` :  
  
```  
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,  
    IDR_HIERSVRTYPE_SRVR_IP, RUNTIME_CLASS(CInPlaceFrame));  
```  
  
 Está listo para ejecutar en contexto en cualquier contenedor que también admite la activación en contexto.  No obstante, habrá un error secundario todavía situada acecho en el código.  HIERSVR admite un menú contextual, que aparece cuando el usuario presiona el botón secundario del mouse.  Este menú funciona cuando HIERSVR es totalmente abierto, pero no funciona al editar una incrustación en contexto.  El motivo se puede anclar abajo a esta línea de código en CServerView::OnRButtonDown:  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x, point.y, AfxGetApp()->m_pMainWnd);  
```  
  
 Observe la referencia a **AfxGetApp\(\)\-\>m\_pMainWnd**.  Cuando el servidor está haber producido en contexto, tiene una ventana principal y se establece el m\_pMainWnd, pero suele ser invisible.  Además, esta ventana hace referencia *a la ventana principal* de la aplicación, la ventana de marco MDI que aparece cuando el servidor está totalmente abiertos o ejecución independiente.  No hace referencia a la ventana de marco activo — que cuando es en contexto generado es una ventana de marco derivada de `COleIPFrameWnd`.  Para obtener la ventana activa correcta aunque la edición en contexto, esta versión de MFC agrega una nueva función, `AfxGetMainWnd`.  En general, debe utilizar esta función en lugar de **AfxGetApp\(\)\-\>m\_pMainWnd**.  Este código debe cambiar como sigue:  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x, point.y, AfxGetMainWnd());  
```  
  
 Ahora tiene un servidor OLE habilitado como mínimo para la activación en contexto funcional.  Pero hay muchas características disponibles con MFC\/OLE 2 que no estaban disponibles en MFC\/OLE1.  Vea el ejemplo HIERSVR para más ideas en características que puede que desee implementar.  Algunas de las características que HIERSVR implementa a continuación:  
  
-   Zoom, para el comportamiento real de WYSISYG en el contenedor.  
  
-   Arrastrar y colocar y un formato personalizado del portapapeles.  
  
-   Se cambia desplazar la ventana contenedora como la selección.  
  
 El ejemplo HIERSVR en MFC 3,0 también utiliza un diseño ligeramente diferente para los elementos del servidor.  Esto ayuda a conservar la memoria y haga los vínculos más flexibles.  Con la versión 2.0 de HIERSVR cada nodo del árbol`COleServerItem`*identidad*.  `COleServerItem` lleva un poco más sobrecarga que estrictamente necesario para cada uno de estos nodos, pero `COleServerItem` se requiere para cada vínculo activo.  Pero en general, hay muy pocos vínculos activos en un momento determinado.  Para crear este más eficaz, el HIERSVR en esta versión de MFC separa el nodo de `COleServerItem`.  Tiene un CServerNode y una clase de **CServerItem** .  **CServerItem** \(derivado de `COleServerItem`\) sólo se crea según sea necesario.  Una vez que la sesión del contenedor \(o contenedores\) con ese vínculo concreto a ese nodo concreto, el objeto de CServerItem asociado al CServerNode se elimina.  Este diseño es más eficaz y flexible.  Su flexibilidad viene en al trabajar con los vínculos de selección múltiple.  Ninguna de estas dos versiones de selección múltiple de compatibilidad HIERSVR, pero se mucho más sencilla de agregar \(y vínculos admiten dichos selecciones\) con la versión de MFC 3,0 HIERSVR, puesto que `COleServerItem` se separa de datos nativos.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)