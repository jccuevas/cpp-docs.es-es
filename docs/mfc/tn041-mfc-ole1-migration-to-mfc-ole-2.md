---
title: 'TN041: Migración de MFC/OLE1 a MFC / OLE 2'
ms.date: 10/18/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: b398a1adbf2f47343eed076f32ade5bb2564cd52
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305455"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: Migración de MFC/OLE1 a MFC/OLE 2

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

## <a name="general-issues-relating-to-migration"></a>Problemas generales relacionados con la migración

Uno de los objetivos de diseño para las clases de OLE 2 en MFC 2.5 (y versiones posteriores) era conservar gran parte de la misma arquitectura que se establecen en MFC 2.0 para la compatibilidad con OLE 1.0. Como resultado, muchas de las mismas clases OLE de MFC 2.0 siguen existan en esta versión de MFC (`COleDocument`, `COleServerDoc`, `COleClientItem`, `COleServerItem`). Además, muchas de las API de estas clases son exactamente iguales. Sin embargo, OLE 2 es radicalmente diferente de OLE 1.0, por lo que puede esperar que han cambiado algunos de los detalles. Si está familiarizado con la compatibilidad con OLE1 de MFC 2.0, se sentirá en casa con el soporte técnico de 2.0 de MFC.

Si está teniendo una aplicación de MFC/OLE1 existente y agregarle funcionalidad OLE 2, debe leer esta nota en primer lugar. Esta nota trata algunos problemas generales que puede surgir al portar su funcionalidad OLE1 a MFC/OLE 2 y, a continuación, describe los problemas detectados durante la migración de dos aplicaciones incluidas en MFC 2.0: los ejemplos OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="mfc-documentview-architecture-is-important"></a>Es importante la arquitectura documento/vista MFC

Si la aplicación no utiliza la arquitectura documento/vista de MFC y desea agregar compatibilidad con OLE 2 a la aplicación, ahora es el momento para desplazarse al documento/vista. Muchas de las ventajas de las clases de MFC OLE 2 se realizan solo una vez que la aplicación utiliza la arquitectura integrado y los componentes de MFC.

Implementar un servidor o un contenedor sin usar la arquitectura de MFC es posible, pero no se recomienda.

## <a name="use-mfc-implementation-instead-of-your-own"></a>Usar la implementación de MFC en lugar de su propio

Las clases MFC "implementación"predefinidos, como `CToolBar`, `CStatusBar`, y `CScrollView` tiene código casos especial integradas para la compatibilidad con OLE 2. Por lo tanto, si puede usar estas clases en la aplicación beneficiará del esfuerzo que se colocan en ellos para que sean OLE compatible con. De nuevo, es posible "rollo de su propio" clases aquí para estos propósitos, pero no se recomienda. Si necesita implementar una funcionalidad similar, el código fuente MFC es una excelente referencia para tratar con algunas de las sutilezas de OLE (especialmente cuando se trata de activación en contexto).

## <a name="examine-the-mfc-sample-code"></a>Examine el código de ejemplo MFC

Hay un número de ejemplos de MFC que incluyen funcionalidad OLE. Cada una de estas aplicaciones implementa OLE de un ángulo diferente:

- [HIERSVR](../overview/visual-cpp-samples.md) pensada principalmente para su uso como una aplicación de servidor. Se incluyó en MFC 2.0 como una aplicación de MFC/OLE1 y haberlo portar a MFC/OLE 2 y, a continuación, extendido, que implementa muchas características OLE disponibles en OLE 2.

- [OCLIENT](../overview/visual-cpp-samples.md) se trata de una aplicación de contenedor independiente, como objetivo mostrar muchas de las características OLE desde la perspectiva del contenedor. También se ha trasladado de la versión 2.0 de MFC y, a continuación, se amplía para admitir muchas de las características más avanzadas de OLE, como los formatos de Portapapeles personalizado y vínculos a los elementos incrustados.

- [DRAWCLI](../overview/visual-cpp-samples.md) esta aplicación implementa compatibilidad con el contenedor OLE mucho como OCLIENT, salvo que lo hace dentro del marco de un programa de dibujo orientada a objetos existente. Se muestra cómo podría implementar la compatibilidad de contenedor OLE e integrarla en su aplicación existente.

- [SUPERPAD](../overview/visual-cpp-samples.md) esta aplicación, así como una aplicación independiente bien, también es un servidor OLE. La compatibilidad de servidor que implementa es muy minimalista. De especial interés es cómo utiliza los servicios del Portapapeles OLE para copiar datos en el Portapapeles, pero usa la funcionalidad integrada en el control de edición"Windows" para implementar la funcionalidad del Portapapeles Pegar. Esto muestra una combinación interesante de uso de la API de Windows tradicionales, así como la integración con las nuevas API OLE.

Para obtener más información sobre las aplicaciones de ejemplo, vea el "ejemplo de Ayuda de MFC".

## <a name="case-study-oclient-from-mfc-20"></a>Caso práctico: OCLIENT de la versión 2.0 de MFC

Como se dijo anteriormente, [OCLIENT](../overview/visual-cpp-samples.md) se incluyó en MFC 2.0 e implementa OLE con MFC/OLE1. Los pasos que inicialmente se convirtió esta aplicación para utilizar las clases MFC/OLE 2 se describen a continuación. Una serie de características se agregaron después de que se completó el puerto inicial para ilustrar mejor las clases MFC/OLE. Estas características no se abordarán; consulte el ejemplo en sí mismo para obtener más información sobre esas características avanzadas.

> [!NOTE]
> Los errores del compilador y el proceso paso a paso se creó con Visual C++ 2.0. Ubicaciones y mensajes de error específicos que pueden haber cambiado con Visual C++ 4.0, pero la información conceptual sigue siendo válida.

## <a name="getting-it-up-and-running"></a>Entre en funcionamiento

Es el enfoque adoptado para portar el ejemplo OCLIENT a MFC/OLE iniciar al crearlo y solucionar los errores del compilador obvio que dará como resultado. Si toma el ejemplo OCLIENT desde MFC 2.0 y compilarlo en esta versión de MFC, encontrará que no hay demasiados errores para resolver. A continuación, se describen los errores en el orden en que se produjeron.

## <a name="compile-and-fix-errors"></a>Errores de compilación y revisión

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

Las primeras preocupaciones para error `COleClientItem::Draw`. En MFC/OLE1 tardó más parámetros de la toma de la versión MFC/OLE. Los parámetros adicionales a menudo no eran necesarios y normalmente es NULL (como se muestra en este ejemplo). Esta versión de MFC puede determinar automáticamente los valores para el lpWBounds cuando es de CDC que se va a dibujar en un DC de metarchivo. Además, el parámetro pFormatDC ya no es necesario puesto que el marco de trabajo creará uno desde el "atributo de controlador de dominio" del pDC pasado. Por lo que para corregir este problema, basta con quitar las dos extra NULL parámetros a la llamada a Draw.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

Los errores por encima del resultado del hecho de que todos los `COleClientItem::CreateXXXX` las funciones de MFC/OLE1 requiere que se pasa un nombre único para representar el elemento. Esto era un requisito de la API OLE subyacente. Esto no es necesario en MFC/OLE 2 como OLE 2 no usa DDE como mecanismo de comunicación subyacente (el nombre se usó en las conversaciones de DDE). Para corregir este problema, puede quitar el `CreateNewName` función, así como todas las referencias a él. Es fácil averiguar lo que cada función MFC/OLE espera en esta versión simplemente, coloque el cursor en la llamada y presione F1.

Otra área que es significativamente diferente es el tratamiento de Portapapeles de OLE 2. Con OLE1, usar el Portapapeles de Windows que las API de interactúan con el Portapapeles. Con OLE 2, esto se realiza con un mecanismo diferente. Las API MFC/OLE1 supone que el Portapapeles estaba abierto antes de copiar un `COleClientItem` objeto en el Portapapeles. Esto ya no es necesario y hará que todas las operaciones del Portapapeles MFC/OLE producir un error. Mientras edita el código para quitar las dependencias en `CreateNewName`, también debe quitar el código que abre y cierra el Portapapeles de Windows.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

Estos errores se producen desde el `CMainView::OnInsertObject` controlador. Controlar el comando "Insertar nuevo objeto" es otra área donde las cosas han cambiado un poco. En este caso, es más fácil simplemente combinar la implementación original con la proporcionada por el Asistente para aplicaciones para una nueva aplicación de contenedor OLE. De hecho, esto es una técnica que se puede aplicar a la migración de otras aplicaciones. En MFC/OLE1, aparece el cuadro de diálogo "Insertar objeto" al llamar a `AfxOleInsertDialog` función. En esta versión se construye un `COleInsertObject` objeto de cuadro de diálogo y llamada `DoModal`. Además, se crean nuevos elementos OLE con una **CLSID** en lugar de una cadena de nombre de clase. El resultado final debe ser similar a esto

```cpp
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
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
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
> Nuevo objeto de inserción puede ser diferente para la aplicación):

También es necesario incluir \<afxodlgs.h >, que contiene la declaración de la `COleInsertObject` clase de cuadro de diálogo, así como los otros cuadros de diálogo estándares proporcionadas por MFC.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

Estos errores se producen por el hecho de que hayan cambiado algunas constantes OLE1 de OLE 2, aunque conceptualmente son iguales. En este caso `OLEVERB_PRIMARY` ha cambiado a `OLEIVERB_PRIMARY`. En OLE1 y OLE 2, normalmente se ejecuta el verbo principal por un contenedor cuando el usuario hace doble clic en un elemento.

Además, `DoVerb` ahora toma un parámetro adicional, un puntero a una vista (`CView`*). Este parámetro solo se usa para implementar "Edición Visual" (o la activación en contexto). Por ahora se establece ese parámetro con valores NULL, porque esta característica no está implementando en este momento.

Para asegurarse de que el marco de trabajo nunca intenta local activa, se debe reemplazar `COleClientItem::CanActivate` como sigue:

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

En MFC/OLE1, `COleClientItem::GetBounds` y `SetBounds` se usaron para consultar y manipular el alcance de un elemento (el `left` y `top` miembros eran siempre cero). En MFC/OLE 2 más directa es compatible con `COleClientItem::GetExtent` y `SetExtent`, que tratar con un **tamaño** o `CSize` en su lugar.

El código para el nuevo SetItemRectToServer, y las llamadas UpdateItemRectFromServer tiene este aspecto:

```cpp
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
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

En API sincrónica de MFC/OLE1 eran las llamadas de un contenedor a un servidor *simulado*, porque OLE1 era intrínsecamente asincrónica en muchos casos. Era necesario para que busque una llamada asincrónica pendiente en curso antes de procesar los comandos del usuario. MFC/OLE1 proporcionados el `COleClientItem::InWaitForRelease` función para hacerlo. En MFC/OLE 2 Esto no es necesario, para que pueda para quitar la invalidación de OnCommand en CMainFrame todos juntos.

En este momento OCLIENT se compile y vincule.

## <a name="other-necessary-changes"></a>Otros cambios necesarios

Hay algunas cosas que no se ha hecho que mantendrá OCLIENT se ejecute, sin embargo. Es mejor corregir estos problemas ahora en lugar de más adelante.

En primer lugar, es necesario inicializar las bibliotecas OLE. Esto se realiza mediante una llamada a `AfxOleInit` desde `InitInstance`:

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

También es una buena idea comprobar para funciones virtuales para los cambios de la lista de parámetros. Una de estas funciones es `COleClientItem::OnChange`invalidado en cada aplicación contenedora MFC/OLE. Si examina la Ayuda en línea, verá que se ha agregado un extra 'DWORD dwParam'. El nuevo CRectItem::OnChange tiene el aspecto siguiente:

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

En MFC/OLE1, aplicaciones de contenedor derivada de la clase de documento `COleClientDoc`. En MFC/OLE 2 ha sido eliminada y reemplazado por esta clase `COleDocument` (esta nueva organización resulta más fácil crear aplicaciones de contenedor y servidor). Hay un **#define** que asigna `COleClientDoc` a `COleDocument` para simplificar la migración de aplicaciones de MFC/OLE1 a MFC/OLE 2, por ejemplo, OCLIENT. Una de las características que no proporcionadas `COleDocument` que proporcionó `COleClientDoc` es el mensaje de comando estándar de entradas de mapa. Esto se realiza de manera que las aplicaciones de servidor, que también usan `COleDocument` (indirectamente), no conlleva la sobrecarga de estos controladores de comando a menos que estén en una aplicación de contenedor y servidor. Deberá agregar las siguientes entradas en el mapa de mensajes CMainDoc:

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

La implementación de todos estos comandos se encuentra en `COleDocument`, que es la clase base para el documento.

En este momento, OCLIENT es una aplicación de contenedor OLE funcional. Es posible insertar elementos de cualquier tipo (OLE1 o OLE 2). Dado que no se implementa el código necesario para habilitar la activación en contexto, editar elementos en una ventana independiente de manera muy similar con OLE1. La siguiente sección describe los cambios necesarios para habilitar la edición en contexto (a veces denominado "Edición Visual").

## <a name="adding-visual-editing"></a>Adición de "Edición Visual"

Una de las características más interesantes de OLE es la activación en contexto (o "Edición Visual"). Esta característica permite que la aplicación de servidor tomar el control de las partes de la interfaz de usuario del contenedor que proporciona una interfaz de edición más sencilla para el usuario. Para implementar la activación en contexto a OCLIENT, algunos recursos especiales deben agregarse, así como código adicional. AppWizard normalmente proporciona estos recursos y el código, de hecho, gran parte de este código se toman prestado directamente en una aplicación mediante AppWizard fresca compatible con el "Contenedor".

En primer lugar, es necesario agregar un recurso de menú que se usará cuando hay un elemento que está activo en contexto. Puede crear este recurso de menú adicionales en Visual C++ copiar el recurso IDR_OCLITYPE y quitando todas excepto los elementos emergentes de archivo y la ventana. Se insertan dos barras separadoras entre los elementos emergentes de archivo y la ventana para indicar la separación de los grupos (debe ser similar: Archivo &#124; &#124; ventana). Para obtener más información sobre lo que significan estos separadores y cómo se combinan los menús de servidor y un contenedor, consulte [menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md).

Una vez que estos menús creados, deberá permitir que el marco de trabajo informara de ello. Esto se realiza mediante una llamada a `CDocTemplate::SetContainerInfo` para la plantilla de documento antes de agregarlo a la lista de plantillas de documento en InitInstance. El nuevo código para registrar la plantilla de documento tiene este aspecto:

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

El recurso IDR_OLECLITYPE_INPLACE es el recurso local especial creado en Visual C++.

Para habilitar la activación en contexto, hay algunas cosas que deben cambiar tanto en el `CView` (CMainView) de clase derivada, así como la `COleClientItem` (CRectItem) de la clase derivada. Todas estas invalidaciones proporcionadas por el Asistente para aplicaciones y la mayoría de la aplicación provendrán directamente de una aplicación de Asistente para aplicaciones de forma predeterminada.

En el primer paso de este puerto, se deshabilitó la activación en contexto mediante la invalidación `COleClientItem::CanActivate`. Este reemplazo debe quitarse para permitir la activación en contexto. Además, se pasa NULL para todas las llamadas a `DoVerb` (hay dos de ellos) porque proporciona la vista solo era necesario para la activación en contexto. Para implementar completamente la activación en contexto, es necesario pasar la vista correcta en el `DoVerb` llamar. Una de estas llamadas se encuentra en `CMainView::OnInsertObject`:

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

Otra es en `CMainView::OnLButtonDblClk`:

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

Es necesario invalidar `COleClientItem::OnGetItemPosition`. Esto indica al servidor dónde colocar la ventana con respecto a la ventana del contenedor cuando el elemento está activado en contexto. Para OCLIENT, la implementación es trivial:

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

Mayoría de los servidores también implementa lo que se denomina "en contexto el cambio de tamaño." Esto permite que la ventana servidores tendrán el tamaño y mover mientras el usuario está editando el elemento. El contenedor debe participar en esta acción, ya que mover o cambiar el tamaño de la ventana normalmente afecta a la posición y tamaño dentro del propio documento contenedor. La implementación para OCLIENT sincroniza el rectángulo interno mantenido por m_rect con la nueva posición y tamaño.

```cpp
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

En este momento, no hay suficiente código para permitir que un elemento se activa en el contexto y para tratar con ajuste de tamaño y mover el elemento cuando está activo, pero ningún código permitirá que el usuario salga de la sesión de edición. Aunque algunos servidores proporcionará esta funcionalidad a sí mismos controlando la tecla escape, se sugiere que los contenedores proporcionan dos maneras de desactivar un elemento: (1) haciendo clic fuera del elemento y (2) si presiona la tecla ESCAPE.

Para la tecla ESCAPE, agregue un acelerador con Visual C++ VK_ESCAPE (clave) que asigna a un comando, ID_CANCEL_EDIT se agrega a los recursos. Sigue el controlador para este comando:

```cpp
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

Para controlar el caso donde el usuario hace clic fuera del elemento, agregue el código siguiente al principio de `CMainView::SetSelection`:

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

Cuando un elemento está activo en contexto, debe tener el foco. Para asegurarse de que este es el caso controlar OnSetFocus para que siempre se transfiere el foco en el elemento activo cuando la vista recibe el foco:

```cpp
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
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

Cuando se cambia el tamaño de la vista, deberá notificar el elemento activo que ha cambiado el rectángulo de recorte. Para ello, proporcione un controlador para `OnSize`:

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>Caso práctico: HIERSVR desde MFC 2.0

[HIERSVR](../overview/visual-cpp-samples.md) también se incluyó en MFC 2.0 e implementa OLE con MFC/OLE1. Esta nota describe brevemente los pasos por el que esta aplicación se convirtió inicialmente para utilizar las clases MFC/OLE 2. Una serie de características se agregaron después de que se completó el puerto inicial para ilustrar mejor las clases MFC/OLE 2. Estas características no se abordarán; consulte el ejemplo en sí mismo para obtener más información sobre esas características avanzadas.

> [!NOTE]
> Los errores del compilador y el proceso paso a paso se creó con Visual C++ 2.0. Ubicaciones y mensajes de error específicos que pueden haber cambiado con Visual C++ 4.0, pero la información conceptual sigue siendo válida.

## <a name="getting-it-up-and-running"></a>Entre en funcionamiento

Es el enfoque adoptado para portar el ejemplo HIERSVR a MFC/OLE iniciar al crearlo y solucionar los errores del compilador obvio que dará como resultado. Si se toma la muestra HIERSVR de MFC 2.0 y compilarlo en esta versión de MFC, encontrará que no hay muchos errores para resolver (aunque hay más de con el ejemplo OCLIENT). Los errores en el orden en que aparecen normalmente se describen a continuación.

## <a name="compile-and-fix-errors"></a>Errores de compilación y revisión

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

Este primer error señala un problema mucho más grande con el `InitInstance` función para los servidores. La inicialización necesaria para un servidor OLE es probablemente uno de los cambios más importantes que tendrá que realizar en la aplicación de MFC/OLE1 a ejecutarlo. Lo mejor es mirar lo que crea el Asistente para aplicaciones de un servidor OLE y modificar el código según corresponda. Estos son algunos puntos a tener en cuenta:

Es necesario inicializar las bibliotecas OLE mediante una llamada a `AfxOleInit`

Llamar a SetServerInfo en el objeto de plantilla de documento para establecer los identificadores de recursos de servidor y la información de clase en tiempo de ejecución que no se puede establecer con el `CDocTemplate` constructor.

No mostrar la ventana principal de la aplicación si /Embedding está presente en la línea de comandos.

Necesitará un **GUID** para el documento. Esto es un identificador único para el tipo de documento (128 bits). AppWizard creará uno automáticamente, por lo que si se usa la técnica descrita aquí consiste en copiar el nuevo código de una nueva aplicación de servidor mediante AppWizard genera, puede simplemente "robar" el GUID de esa aplicación. Si no es así, puede usar el GUIDGEN. Utilidad EXE en el directorio BIN.

Es necesario "conectar" su `COleTemplateServer` objeto a la plantilla de documento mediante una llamada a `COleTemplateServer::ConnectTemplate`.

Actualizar el registro del sistema cuando se ejecuta la aplicación independiente. De esta forma, si el usuario mueve el. EXE para la aplicación, ejecutarlo desde su nueva ubicación se actualizará la base de datos de registro de sistema de Windows para que apunte a la nueva ubicación.

Después de aplicar todos estos cambios en función de lo que crea el Asistente para aplicaciones para `InitInstance`, el `InitInstance` (y relacionados con el GUID) para HIERSVR debe indicar lo siguiente:

```cpp
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
    LoadStdProfileSettings();   // Load standard INI file options

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

    SetDialogBkColor(); // gray look

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

Observará que el código anterior hace referencia a un nuevo identificador de recurso, IDR_HIERSVRTYPE_SRVR_EMB. Este es el recurso de menú que se usará cuando se modifica un documento que está incrustado en otro contenedor. En MFC/OLE1 se modificaron los elementos de menú específicos para editar un elemento incrustado sobre la marcha. Mediante una estructura de menú totalmente diferente al editar un elemento incrustado en lugar de editar un documento basado en archivo resulta mucho más sencillo proporcionar interfaces de usuario diferentes para estos dos modos independientes. Como verá más adelante, se usa un recurso de menú totalmente independiente al editar un objeto incrustado en contexto.

Para crear este recurso, cargar el script de recursos en Visual C++ y copiar el recurso de menú IDR_HIERSVRTYPE existente. Cambie el nombre del nuevo recurso IDR_HIERSVRTYPE_SRVR_EMB (esta es la misma convención de nomenclatura que utiliza el Asistente para aplicaciones). A continuación cambie "Guardar archivo" para "Actualización del archivo"; asígnele ID_FILE_UPDATE de Id. de comando. También cambiar "Guardar archivo como" a "Archivo Guardar copia como"; asígnele ID_FILE_SAVE_COPY_AS de Id. de comando. El marco de trabajo proporciona la implementación de ambos de estos comandos.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

Hay una serie de errores resultantes de la invalidación de `OnSetData`, ya que hace referencia a la **OLESTATUS** tipo. **OLESTATUS** era la forma OLE1 devuelve errores. Esto ha cambiado a **HRESULT** en OLE 2, aunque MFC normalmente convierte un **HRESULT** en un `COleException` que contiene el error. En este caso concreto, la invalidación de `OnSetData` ya no es necesario, por lo que es lo más fácil quitarlo.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

El `COleServerItem` constructor toma un parámetro de 'tipo BOOL' adicional. Este indicador determina cómo se realiza la administración de memoria en el `COleServerItem` objetos. Si se establece en TRUE, el marco de trabajo controla la administración de memoria de estos objetos, eliminándolos cuando ya no son necesarios. Usa HIERSVR `CServerItem` (derivado de `COleServerItem`) objetos como parte de sus datos nativos, por lo que deberá establecer esta marca en FALSE. Esto permite HIERSVR determinar cuando se elimina cada elemento del servidor.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

Tal como implican estos errores, hay algunas funciones 'virtuales puras' que no se han reemplazado en CServerItem. Probablemente esto se debe al hecho de que ha cambiado la lista de parámetros de OnDraw. Para corregir este error, cambie `CServerItem::OnDraw` como sigue (así como la declaración en svritem.h):

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

El nuevo parámetro es 'rSize'. Esto permite que rellene el tamaño del dibujo, si es conveniente. Este tamaño debe estar en **HIMETRIC**. En este caso, no es conveniente rellenar este valor, por lo que el marco llama a `OnGetExtent` para recuperar la extensión. Para que funcione, debe implementar `OnGetExtent`:

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

En la función CServerItem::CalcNodeSize el tamaño del elemento se convierte en **HIMETRIC** y se almacenan en *m_rectBounds*. El indocumentados '*m_rectBounds*' miembro de `COleServerItem` no existe (se ha reemplazado parcialmente por *m_sizeExtent*, pero en OLE 2 este miembro tiene un uso ligeramente diferente que *m_rectBounds* en OLE1). En lugar de establecer el **HIMETRIC** tamaño en esta variable miembro, podrá devolverla. Este valor devuelto se usa en `OnGetExtent`, implementadas previamente.

```cpp
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

También invalida CServerItem `COleServerItem::OnGetTextData`. Esta función está obsoleta en MFC/OLE y se reemplaza por un mecanismo diferente. La versión 3.0 de MFC de OLE de MFC muestra [HIERSVR](../overview/visual-cpp-samples.md) implementa esta funcionalidad mediante la invalidación `COleServerItem::OnRenderFileData`. Esta funcionalidad no es importante para este puerto básica, para poder quitar la invalidación OnGetTextData.

Hay muchos más errores en svritem.cpp que no se han solucionado. No son errores "reales", solo a los errores causado por errores anteriores.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` ya no es compatible con la `bIncludeNative` marca. Siempre se copian los datos nativos (es decir, los datos escritos por la función Serialize del elemento servidor), para quitar el primer parámetro. Además, `CopyToClipboard` se iniciará una excepción cuando se produce un error en lugar de devolver FALSE. Cambie el código para CServerView::OnEditCopy como sigue:

```cpp
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

Aunque hubo más errores resultantes de la compilación de la versión 2.0 de MFC de HIERSVR que había para la misma versión de OCLIENT, hubo realmente menos cambios.

En este momento HIERSVR compilará y vincular y funcione como un servidor OLE, pero sin la característica de edición en contexto, que se implementará a continuación.

## <a name="adding-visual-editing"></a>Adición de "Edición Visual"

Para agregar "Edición Visual" (o la activación en contexto) para esta aplicación de servidor, hay sólo algunas cosas que debe tener cuidado de:

- Se necesita un recurso de menú especial que se usará cuando el elemento está activo en contexto.

- Esta aplicación tiene una barra de herramientas, por lo que tendrá una barra de herramientas con solo un subconjunto de la barra de herramientas normal para que coincida con los comandos de menú disponibles en el servidor (coincide con el recurso de menú que se mencionó anteriormente).

- Necesita una clase nueva derivada de `COleIPFrameWnd` que proporciona la interfaz de usuario local (de forma similar a CMainFrame, derivado de `CMDIFrameWnd`, proporciona la interfaz de usuario MDI).

- Deberá indicar al marco sobre estos recursos especiales y las clases.

Es fácil crear el recurso de menú. Ejecute Visual C++, copiar el recurso de menú IDR_HIERSVRTYPE a un recurso de menú denominado IDR_HIERSVRTYPE_SRVR_IP. Modifique el menú para que se mantienen solo la edición y ayudarle a menús contextuales. Agregar dos separadores al menú entre los menús de edición y la Ayuda (que debería ser similar: Editar &#124; &#124; ayuda). Para obtener más información sobre lo que significan estos separadores y cómo se combinan los menús de servidor y un contenedor, consulte [menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md).

El mapa de bits de la barra de herramientas del subconjunto se puede crear fácilmente mediante la copia de una nueva aplicación AppWizard genera con una opción "Servidor" activada. Este mapa de bits, a continuación, puede importarse en Visual C++. Asegúrese de dar el mapa de bits en un Id. de IDR_HIERSVRTYPE_SRVR_IP.

La clase derivada de `COleIPFrameWnd` pueden copiarse desde una aplicación mediante AppWizard genera con también compatibilidad con el servidor. Copie ambos archivos, IPFRAME. CPP y IPFRAME. H y agregarlos al proyecto. Asegúrese de que el `LoadBitmap` llamada hace referencia a IDR_HIERSVRTYPE_SRVR_IP, el mapa de bits que se creó en el paso anterior.

Ahora que se crean todos los nuevos recursos y clases, agregue el código necesario para que el marco de trabajo sabe acerca de estos (y sabe que esta aplicación ahora admite la edición en contexto). Esto se realiza mediante la adición de algunos parámetros más a la `SetServerInfo` llamar el `InitInstance` función:

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

Ahora está listo para ejecutarse en el lugar en cualquier contenedor que también admite la activación en contexto. Sin embargo, hay un error menor que aún se encuentren en el código. HIERSVR admite un menú contextual, que se muestra cuando el usuario presiona el botón secundario del mouse. Este menú funciona cuando HIERSVR está totalmente abierto, pero no funciona cuando se edita un inserción en el lugar. El motivo se puede anclar en esta línea de código en CServerView::OnRButtonDown:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

Tenga en cuenta la referencia a `AfxGetApp()->m_pMainWnd`. Cuando el servidor está activado en contexto, tiene una ventana principal y se establece m_pMainWnd, pero resulta suele pasar desapercibido. Además, esta ventana se refiere a la *principal* ventana de la aplicación, abra o ejecutarse de forma independiente de la ventana de marco MDI que aparece cuando el servidor está totalmente. No hace referencia a la ventana de marco activo, que cuando local activa es un marco de ventana deriva `COleIPFrameWnd`. Para obtener la ventana activa correcta incluso cuando la edición en contexto, esta versión de MFC se agrega una nueva función, `AfxGetMainWnd`. Por lo general, debe usar esta función en lugar de `AfxGetApp()->m_pMainWnd`. Este código debe cambiar como sigue:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

Ahora tiene un servidor OLE mínimamente habilitado para la activación en contexto funcional. Pero todavía hay muchas características disponibles con MFC/OLE 2 que no estaban disponibles en MFC/OLE1. Vea el ejemplo HIERSVR para obtener más ideas sobre las características que desea implementar. Algunas de las características que implementa HIERSVR se enumeran a continuación:

- Zoom para el comportamiento de WYSIWYG true en relación con el contenedor.

- Arrastrar y colocar y un formato de Portapapeles personalizado.

- Se cambia el desplazamiento de la ventana del contenedor como la selección.

El ejemplo HIERSVR en MFC 3.0 también usa un diseño ligeramente diferente para los elementos del servidor. Esto ayuda a conservar memoria y hace que los vínculos más flexible. Con la versión 2.0 de HIERSVR cada nodo del árbol *es un* `COleServerItem`. `COleServerItem` lleva a cabo un poco más sobrecarga que es estrictamente necesario para cada uno de estos nodos, pero un `COleServerItem` es necesaria para cada vínculo activo. Pero en su mayor parte, hay muy pocos vínculos activos en un momento dado. Para que esto resulte más eficaz, el archivo HIERSVR en esta versión de MFC separa el nodo desde el `COleServerItem`. Tiene tanto un CServerNode y un `CServerItem` clase. El `CServerItem` (derivado de `COleServerItem`) solo se crea según sea necesario. Una vez que el contenedor (o contenedores) deja de usar ese vínculo concreto para ese nodo concreto, se elimina el objeto CServerItem asociado con el CServerNode. Este diseño es más eficaz y más flexible. Su flexibilidad resulta cuando se trabaja con varios vínculos de selección. Ninguna de estas dos versiones de HIERSVR admiten selección múltiple, pero sería mucho más fácil agregar (y para admitir vínculos a estas selecciones) con la versión 3.0 de MFC de HIERSVR, puesto que la `COleServerItem` se separa de los datos nativos.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
