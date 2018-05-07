---
title: Clase COleDocument | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
dev_langs:
- C++
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6317d7c14f76355df908c9809df633533df3fb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="coledocument-class"></a>COleDocument (clase)
La clase base para los documentos de OLE que admiten la edición visual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|Construye un objeto `COleDocument`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|Agrega un elemento a la lista de elementos que se mantiene el documento.|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Establece el dispositivo de destino de impresión para todos los elementos de cliente en el documento.|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Hace que los documentos que se almacenará con el formato de archivo de almacenamiento estructurado OLE.|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Devuelve el elemento OLE que está activo actualmente en el contexto.|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|Obtiene el siguiente elemento de cliente para efectuar una iteración.|  
|[COleDocument::GetNextItem](#getnextitem)|Obtiene el siguiente elemento de documento para efectuar una iteración.|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|Obtiene el siguiente elemento del servidor para efectuar una iteración.|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Devuelve el elemento principal de OLE seleccionado en el documento.|  
|[COleDocument::GetStartPosition](#getstartposition)|Obtiene la posición inicial para iniciar la iteración.|  
|[COleDocument::HasBlankItems](#hasblankitems)|Comprueba si hay elementos en blanco en el documento.|  
|[COleDocument::OnShowViews](#onshowviews)|Se llama cuando el documento se vuelve visible o invisible.|  
|[COleDocument::RemoveItem](#removeitem)|Quita un elemento de la lista de elementos que se mantiene el documento.|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Marca el documento como modificado si cualquiera de los elementos OLE contenidos se han modificado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Controla los eventos en el comando de menú del icono de cambio.|  
|[COleDocument::OnEditConvert](#oneditconvert)|Controla la conversión de un objeto incrustado o vinculado de un tipo a otro.|  
|[COleDocument::OnEditLinks](#oneditlinks)|Controla los eventos en el comando vínculos en el menú Edición.|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo electrónico con el documento adjunto.|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Lo llama el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Editar/Cambiar icono.|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Lo llama el marco de trabajo para actualizar el comando de la interfaz de usuario para la opción de menú Editar/vínculos.|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Lo llama el marco para actualizar la interfaz de usuario de comandos para la edición / *ObjectName* opción de menú y el submenú de verbo que se tiene acceso desde edición / *ObjectName*.|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Lo llama el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Pegado especial.|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Lo llama el marco de trabajo para actualizar el comando de la interfaz de usuario para la opción de menú de pegar.|  
  
## <a name="remarks"></a>Comentarios  
 `COleDocument` se deriva de **CDocument**, que permite que las aplicaciones OLE se utiliza la arquitectura documento/vista proporcionada por la biblioteca Microsoft Foundation Class.  
  
 `COleDocument` trata de un documento como una colección de [CDocItem](../../mfc/reference/cdocitem-class.md) objetos para procesar elementos OLE. El contenedor y servidor de aplicaciones requieren una arquitectura tan porque sus documentos deben ser capaz de contener elementos OLE. El [COleServerItem](../../mfc/reference/coleserveritem-class.md) y [COleClientItem](../../mfc/reference/coleclientitem-class.md) clases, ambas derivadas de `CDocItem`, administrar las interacciones entre las aplicaciones y elementos OLE.  
  
 Si está escribiendo una aplicación de contenedor simple, derive su clase de documento de `COleDocument`. Si está escribiendo una aplicación de contenedor que admite la vinculación a los elementos incrustados contenidos en sus documentos, derive su clase de documento de [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Si está escribiendo un servidor de aplicación o combinación contenedor/servidor, derive su clase de documento de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` y `COleServerDoc` derivadas de `COleDocument`, por lo que estas clases heredan todos los servicios disponibles en `COleDocument` y **CDocument**.  
  
 Para usar `COleDocument`, derive una clase de ella y agregar la funcionalidad para administrar la aplicación los datos no son compatibles con OLE, así como elementos incrustados o vinculados. Si define `CDocItem`-sus clases derivadas para almacenar datos nativos de la aplicación, puede usar la implementación predeterminada definida por `COleDocument` para almacenar los datos no son compatibles con OLE y OLE. También puede diseñar sus propias estructuras de datos para almacenar los datos no son compatibles con OLE por separado de los elementos OLE. Para obtener más información, vea el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md)...  
  
 **CDocument** admite el envío de documentos a través de correo electrónico si hay compatibilidad de correo (MAPI). `COleDocument` actualizó [OnFileSendMail](#onfilesendmail) para administrar documentos compuestos correctamente. Para obtener más información, vea los artículos [MAPI](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="additem"></a>  COleDocument::AddItem  
 Llame a esta función para agregar un elemento al documento.  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Puntero para el elemento de documento que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 No es necesario llamar explícitamente a esta función cuando se llama la `COleClientItem` o `COleServerItem` constructor que acepte un puntero a un documento.  
  
##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice  
 Llame a esta función para cambiar el dispositivo de destino de impresión para todos los incrustados [COleClientItem](../../mfc/reference/coleclientitem-class.md) elementos en el documento del contenedor de la aplicación.  
  
```  
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptd`  
 Puntero a un **DVTARGETDEVICE** estructuras de datos que contiene información sobre el nuevo dispositivo de destino de impresión. Puede ser **NULL**.  
  
 `ppd`  
 Puntero a un **PRINTDLG** estructuras de datos que contiene información sobre el nuevo dispositivo de destino de impresión. Puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función actualiza el dispositivo de destino de impresión para todos los elementos, pero no actualiza la caché de presentación para los elementos. Para actualizar la caché de presentación para un elemento, llame a [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).  
  
 Los argumentos a esta función contienen información que OLE se usa para identificar el dispositivo de destino. El [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) estructura contiene información que Windows usa para inicializar el cuadro de diálogo de impresión comunes. Después de que el usuario cierra el cuadro de diálogo, Windows devuelve información acerca de las selecciones del usuario en esta estructura. El `m_pd` miembro de un [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objeto es un **PRINTDLG** estructura.  
  
 Para obtener más información, consulte el [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) estructura en el SDK de Windows.  
  
 Para obtener más información, consulte el [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) estructura en el SDK de Windows.  
  
##  <a name="coledocument"></a>  COleDocument::COleDocument  
 Construye un objeto `COleDocument`.  
  
```  
COleDocument();
```  
  
##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile  
 Llame a esta función si desea almacenar el documento con el formato de archivo compuesto.  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 Especifica si la compatibilidad con archivos compuestos está habilitada o deshabilitada.  
  
### <a name="remarks"></a>Comentarios  
 También se denomina almacenamiento estructurado. Se suele llamar a esta función desde el constructor de la `COleDocument`-clase derivada. Para obtener más información acerca de los documentos compuestos, vea el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md)...  
  
 Si no se llama a esta función miembro, los documentos se almacenará en un formato de archivo ("plano") no estructurados.  
  
 Después de soporte técnico de archivo compuesto está habilitada o deshabilitada para un documento, el valor no debe cambiarse durante la duración del documento.  
  
##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem  
 Llamada a esta función para obtener el OLE de elemento que está activada actualmente en su lugar en la ventana de marco que contiene la vista identificada por `pWnd`.  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que muestra el documento contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la único, en lugar OLE elemento activo; **NULL** si no hay ningún elemento OLE actualmente en el estado de "activo en contexto".  
  
##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem  
 Llame a esta función repetidamente con el fin de obtener acceso a cada uno de los elementos de cliente en el documento.  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Una referencia a un **posición** valor establecido por una llamada anterior a `GetNextClientItem`; el valor inicial es devuelto por la `GetStartPosition` función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al siguiente elemento de cliente en el documento, o **NULL** si no hay más elementos de cliente.  
  
### <a name="remarks"></a>Comentarios  
 Después de cada llamada, el valor de `pos` se establece para el elemento siguiente en el documento, que puede ser o no un elemento de cliente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="getnextitem"></a>  COleDocument::GetNextItem  
 Llame a esta función repetidamente con el fin de obtener acceso a cada uno de los elementos del documento.  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Una referencia a un **posición** valor establecido por una llamada anterior a `GetNextItem`; el valor inicial es devuelto por la `GetStartPosition` función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de documento en la posición especificada.  
  
### <a name="remarks"></a>Comentarios  
 Después de cada llamada, el valor de `pos` está establecido en el **posición** valor del elemento siguiente en el documento. Si el elemento recuperado es el último elemento en el documento, el nuevo valor de `pos` es **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem  
 Llame a esta función repetidamente con el fin de obtener acceso a cada uno de los elementos del servidor en el documento.  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Una referencia a un **posición** valor establecido por una llamada anterior a `GetNextServerItem`; el valor inicial es devuelto por la `GetStartPosition` función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al siguiente elemento de servidor en el documento, o **NULL** si no hay más elementos de servidor.  
  
### <a name="remarks"></a>Comentarios  
 Después de cada llamada, el valor de `pos` se establece para el elemento siguiente en el documento, que puede ser o no un elemento del servidor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem  
 Lo llama el marco de trabajo para recuperar el elemento OLE actualmente seleccionado en la vista especificada.  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>Parámetros  
 `pView`  
 Puntero al objeto de vista activa muestra el documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento OLE único, seleccionado; **NULL** si se seleccionó ningún elemento OLE o si hay más de uno está seleccionada.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada busca elementos para un único elemento seleccionado en la lista de OLE independiente y devuelve un puntero a ella. Si no hay ningún elemento seleccionado, o si hay más de un elemento seleccionado, la función devuelve **NULL**. Es necesario reemplazar el `CView::IsSelected` función miembro en la clase de vista para esta función se ejecute correctamente. Reemplace esta función si tiene su propio método para almacenar elementos OLE contenidos.  
  
##  <a name="getstartposition"></a>  COleDocument::GetStartPosition  
 Llame a esta función para obtener la posición del primer elemento en el documento.  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que puede utilizarse para empezar a recorrer en iteración los elementos del documento; **NULL** si el documento no tiene ningún elemento.  
  
### <a name="remarks"></a>Comentarios  
 Pasar el valor devuelto a `GetNextItem`, `GetNextClientItem`, o `GetNextServerItem`.  
  
##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems  
 Llame a esta función para determinar si el documento contiene todos los elementos en blanco.  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el documento contiene algún elemento en blanco; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un elemento en blanco es uno cuyo rectángulo está vacío.  
  
##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon  
 Muestra el cuadro de diálogo de OLE Cambiar icono y se cambia el icono que representa el elemento OLE actualmente seleccionado en el icono que el usuario selecciona en el cuadro de diálogo.  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>Comentarios  
 `OnEditChangeIcon` crea e inicia un `COleChangeIconDialog` cuadro de diálogo Cambiar icono.  
  
##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert  
 Muestra el cuadro de diálogo Convertir OLE y convierte o activa el elemento seleccionado actualmente de OLE según las selecciones del usuario en el cuadro de diálogo.  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>Comentarios  
 `OnEditConvert` crea e inicia un `COleConvertDialog` cuadro de diálogo convertir.  
  
 Un ejemplo de conversión convierte un documento de Microsoft Word en un documento de WordPad.  
  
##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks  
 Muestra el cuadro de diálogo de OLE/vínculos de edición.  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>Comentarios  
 `OnEditLinks` crea e inicia un `COleLinksDialog` cuadro de diálogo de vínculos que permite al usuario cambiar los objetos vinculados.  
  
##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail  
 Envía un mensaje a través del host de correo electrónico residente (si existe) con el documento como datos adjuntos.  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>Comentarios  
 `OnFileSendMail` llamadas `OnSaveDocument` para serializar (documentos sin título y modificados en un archivo temporal, que se envía a través de correo electrónico Guardar). Si el documento no se ha modificado, no se necesita un archivo temporal; se envía el original. `OnFileSendMail` carga MAPI32. Archivo DLL si aún no se haya cargado.  
  
 A diferencia de la implementación de `OnFileSendMail` para **CDocument**, esta función controla archivos compuestos correctamente.  
  
 Para obtener más información, consulte el [temas de MAPI](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md) artículos...  
  
##  <a name="onshowviews"></a>  COleDocument::OnShowViews  
 El marco de trabajo llama a esta función después de la visibilidad del documento cambios de estado.  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>Parámetros  
 `bVisible`  
 Indica si el documento se ha convertido en visible o invisible.  
  
### <a name="remarks"></a>Comentarios  
 La versión predeterminada de esta función no hace nada. Reemplácelo si su aplicación debe realizar cualquier procesamiento especial cuando cambia la visibilidad del documento.  
  
##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon  
 Lo llama el marco de trabajo para actualizar el comando Cambiar icono en el menú Edición.  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a un `CCmdUI` estructura que representa el menú que generó el comando de actualización. Las llamadas del controlador de actualización de la **habilitar** función miembro de la `CCmdUI` a través de la estructura `pCmdUI` para actualizar la interfaz de usuario.  
  
### <a name="remarks"></a>Comentarios  
 `OnUpdateEditChangeIcon` actualiza la interfaz de usuario del comando dependiendo de si existe o no un icono válido en el documento. Reemplace esta función para cambiar el comportamiento.  
  
##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu  
 Lo llama el marco de trabajo para actualizar el comando vínculos en el menú Edición.  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a un `CCmdUI` estructura que representa el menú que generó el comando de actualización. Las llamadas del controlador de actualización de la **habilitar** función miembro de la `CCmdUI` a través de la estructura `pCmdUI` para actualizar la interfaz de usuario.  
  
### <a name="remarks"></a>Comentarios  
 A partir del primer elemento OLE en el documento, `OnUpdateEditLinksMenu` tiene acceso a cada elemento, comprueba si el elemento es un vínculo y, si se trata de un vínculo, habilita el comando de vínculos. Reemplace esta función para cambiar el comportamiento.  
  
##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu  
 Lo llama el marco para actualizar la *ObjectName* comando en el menú de edición y el submenú de verbo que se tiene acceso desde el *ObjectName* comando, donde *ObjectName* es el nombre de el objeto OLE incrustado en el documento.  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a un `CCmdUI` estructura que representa el menú que generó el comando de actualización. Las llamadas del controlador de actualización de la **habilitar** función miembro de la `CCmdUI` a través de la estructura `pCmdUI` para actualizar la interfaz de usuario.  
  
### <a name="remarks"></a>Comentarios  
 `OnUpdateObjectVerbMenu` las actualizaciones de la *ObjectName* interfaz de usuario del comando dependiendo de si existe o no un objeto válido en el documento. Si existe un objeto, el *ObjectName* está habilitado el comando en el menú Edición. Cuando se selecciona este comando de menú, se muestra el submenú de verbo. El submenú de verbo contiene todos los comandos de verbo disponibles para el objeto, por ejemplo, editar, propiedades y así sucesivamente. Reemplace esta función para cambiar el comportamiento.  
  
##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu  
 Lo llama el marco de trabajo para determinar si un elemento OLE vinculado se puede pegar desde el Portapapeles.  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a un `CCmdUI` estructura que representa el menú que generó el comando de actualización. Las llamadas del controlador de actualización de la **habilitar** función miembro de la `CCmdUI` a través de la estructura `pCmdUI` para actualizar la interfaz de usuario.  
  
### <a name="remarks"></a>Comentarios  
 El comando de menú Pegado especial se habilita o deshabilita dependiendo de si se puede pegar el elemento en el documento o no.  
  
##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu  
 Lo llama el marco de trabajo para determinar si un elemento OLE incrustado se puede pegar del Portapapeles.  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a un `CCmdUI` estructura que representa el menú que generó el comando de actualización. Las llamadas del controlador de actualización de la **habilitar** función miembro de la `CCmdUI` a través de la estructura `pCmdUI` para actualizar la interfaz de usuario.  
  
### <a name="remarks"></a>Comentarios  
 El comando de menú de pegar y el botón se habilita o deshabilita dependiendo de si se puede pegar el elemento en el documento o no.  
  
##  <a name="removeitem"></a>  COleDocument::RemoveItem  
 Llame a esta función para quitar un elemento del documento.  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Puntero a los elementos de documento que va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente no es necesario llamar a esta función explícitamente; se llama a los destructores de `COleClientItem` y `COleServerItem`.  
  
##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag  
 Llame a esta función para marcar el documento como modificado si cualquiera de los elementos OLE contenidos se han modificado.  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto permite que el marco de trabajo solicitar al usuario que guarde el documento antes de cerrarlo, incluso si no se ha modificado los datos nativos en el documento.  
  
## <a name="see-also"></a>Vea también  
 [Aplicación de ejemplo CONTAINER](../../visual-cpp-samples.md)   
 [Ejemplo MFC MFCBIND](../../visual-cpp-samples.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



