---
title: COleDocument (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: b92c796fdaa972966dcbfa85b1e34f267b6c629c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426496"
---
# <a name="coledocument-class"></a>COleDocument (clase)

La clase base para los documentos de OLE que admiten la edición visual.

## <a name="syntax"></a>Sintaxis

```
class COleDocument : public CDocument
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDocument:: COleDocument](#coledocument)|Construye un objeto `COleDocument`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDocument:: AddItem](#additem)|Agrega un elemento a la lista de elementos que mantiene el documento.|
|[COleDocument:: ApplyPrintDevice](#applyprintdevice)|Establece el dispositivo de destino de impresión para todos los elementos de cliente del documento.|
|[COleDocument:: EnableCompoundFile](#enablecompoundfile)|Hace que los documentos se almacenen con el formato de archivo de almacenamiento estructurado OLE.|
|[COleDocument:: GetInPlaceActiveItem](#getinplaceactiveitem)|Devuelve el elemento OLE actualmente activo en contexto.|
|[COleDocument:: GetNextClientItem](#getnextclientitem)|Obtiene el siguiente elemento de cliente para la iteración.|
|[COleDocument:: GetNextItem](#getnextitem)|Obtiene el siguiente elemento de documento para la iteración.|
|[COleDocument:: GetNextServerItem](#getnextserveritem)|Obtiene el siguiente elemento de servidor para la iteración.|
|[COleDocument:: GetPrimarySelectedItem](#getprimaryselecteditem)|Devuelve el elemento OLE seleccionado principal del documento.|
|[COleDocument:: GetStartPosition](#getstartposition)|Obtiene la posición inicial para comenzar la iteración.|
|[COleDocument:: HasBlankItems](#hasblankitems)|Comprueba si hay elementos en blanco en el documento.|
|[COleDocument:: OnShowViews](#onshowviews)|Se llama cuando el documento se vuelve visible o invisible.|
|[COleDocument:: RemoveItem](#removeitem)|Quita un elemento de la lista de elementos mantenidos por el documento.|
|[COleDocument:: UpdateModifiedFlag](#updatemodifiedflag)|Marca el documento como modificado si se ha modificado alguno de los elementos OLE contenidos.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleDocument:: OnEditChangeIcon](#oneditchangeicon)|Controla los eventos del comando de menú Cambiar icono.|
|[COleDocument:: OnEditConvert](#oneditconvert)|Controla la conversión de un objeto incrustado o vinculado de un tipo a otro.|
|[COleDocument:: OnEditLinks](#oneditlinks)|Controla los eventos del comando links en el menú edición.|
|[COleDocument:: OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo electrónico con el documento adjunto.|
|[COleDocument:: OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Lo llama el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Editar/cambiar icono.|
|[COleDocument:: OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Lo llama el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Editar/vínculos.|
|[COleDocument:: OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Lo llama el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Editar/ *objectname* y el submenú de verbo al que se tiene acceso desde Edit/ *objectname*.|
|[COleDocument:: OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Lo llama el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú pegar especial.|
|[COleDocument:: OnUpdatePasteMenu](#onupdatepastemenu)|Lo llama el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú pegar.|

## <a name="remarks"></a>Observaciones

`COleDocument` se deriva de `CDocument`, lo que permite que las aplicaciones OLE utilicen la arquitectura documento/vista proporcionada por el biblioteca MFC.

`COleDocument` trata un documento como una colección de objetos [CDocItem](../../mfc/reference/cdocitem-class.md) para controlar elementos OLE. Tanto las aplicaciones de contenedor como de servidor requieren este tipo de arquitectura, ya que sus documentos deben ser capaces de contener elementos OLE. Las clases [COleServerItem](../../mfc/reference/coleserveritem-class.md) y [COleClientItem](../../mfc/reference/coleclientitem-class.md) , tanto derivadas de `CDocItem`, administran las interacciones entre las aplicaciones y los elementos OLE.

Si está escribiendo una aplicación contenedora sencilla, derive la clase de documento de `COleDocument`. Si está escribiendo una aplicación contenedora que admite la vinculación a los elementos incrustados contenidos en sus documentos, derive la clase de documento de [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Si está escribiendo una aplicación de servidor o una combinación de contenedor/servidor, derive la clase de documento de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` y `COleServerDoc` se derivan de `COleDocument`, por lo que estas clases heredan todos los servicios disponibles en `COleDocument` y `CDocument`.

Para usar `COleDocument`, derive una clase a partir de ella y agregue funcionalidad para administrar los datos no OLE de la aplicación, así como elementos incrustados o vinculados. Si define clases derivadas de `CDocItem`para almacenar los datos nativos de la aplicación, puede usar la implementación predeterminada definida por `COleDocument` para almacenar los datos OLE y los no OLE. También puede diseñar sus propias estructuras de datos para almacenar los datos que no son de OLE por separado de los elementos OLE. Para obtener más información, vea el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md).

`CDocument` admite el envío de un documento a través de mail, si la compatibilidad con correo (MAPI) está presente. `COleDocument` ha actualizado [OnFileSendMail](#onfilesendmail) para que los documentos compuestos se controlen correctamente. Para obtener más información, vea los artículos compatibilidad con [MAPI](../../mfc/mapi.md) y [MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[Reemplaza](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="additem"></a>COleDocument:: AddItem

Llame a esta función para agregar un elemento al documento.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento que se va a agregar.

### <a name="remarks"></a>Observaciones

No es necesario llamar a esta función explícitamente cuando lo llama el constructor `COleClientItem` o `COleServerItem` que acepta un puntero a un documento.

##  <a name="applyprintdevice"></a>COleDocument:: ApplyPrintDevice

Llame a esta función para cambiar el dispositivo de destino de impresión para todos los elementos [COleClientItem](../../mfc/reference/coleclientitem-class.md) incrustados en el documento de contenedor de la aplicación.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parámetros

*fichero*<br/>
Puntero a una estructura de datos `DVTARGETDEVICE`, que contiene información sobre el nuevo dispositivo de destino de impresión. Puede ser NULL.

*PDD*<br/>
Puntero a una estructura de datos `PRINTDLG`, que contiene información sobre el nuevo dispositivo de destino de impresión. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función actualiza el dispositivo de destino de impresión para todos los elementos, pero no actualiza la caché de presentación de esos elementos. Para actualizar la memoria caché de presentación de un elemento, llame a [COleClientItem:: UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Los argumentos de esta función contienen información que OLE usa para identificar el dispositivo de destino. La estructura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) contiene información que Windows usa para inicializar el cuadro de diálogo de impresión común. Una vez que el usuario cierra el cuadro de diálogo, Windows devuelve información acerca de las selecciones del usuario en esta estructura. El miembro `m_pd` de un objeto [CPrintDialog](../../mfc/reference/cprintdialog-class.md) es una estructura de `PRINTDLG`.

Para obtener más información, vea la estructura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) en el Windows SDK.

Para obtener más información, vea la estructura [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) en el Windows SDK.

##  <a name="coledocument"></a>COleDocument:: COleDocument

Construye un objeto `COleDocument`.

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>COleDocument:: EnableCompoundFile

Llame a esta función si desea almacenar el documento con el formato de archivo compuesto.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
Especifica si la compatibilidad con archivos compuestos está habilitada o deshabilitada.

### <a name="remarks"></a>Observaciones

Esto también se denomina almacenamiento estructurado. Normalmente, se llama a esta función desde el constructor de la clase derivada de `COleDocument`. Para obtener más información sobre los documentos compuestos, vea el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md).

Si no llama a esta función miembro, los documentos se almacenarán en un formato de archivo no estructurado ("plano").

Una vez habilitada o deshabilitada la compatibilidad con archivos compuestos para un documento, la configuración no debe cambiarse durante la vigencia del documento.

##  <a name="getinplaceactiveitem"></a>COleDocument:: GetInPlaceActiveItem

Llame a esta función para obtener el elemento OLE actualmente activado en su lugar en la ventana de marco que contiene la vista identificada por *PWND*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que muestra el documento contenedor.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento OLE activo único en contexto; Es NULL si no hay ningún elemento OLE actualmente en el estado "en contexto activo".

##  <a name="getnextclientitem"></a>COleDocument:: GetNextClientItem

Llame a esta función varias veces para tener acceso a cada uno de los elementos de cliente del documento.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*pos*<br/>
Referencia a un valor de posición establecido por una llamada anterior a `GetNextClientItem`; la función miembro `GetStartPosition` devuelve el valor inicial.

### <a name="return-value"></a>Valor devuelto

Puntero al siguiente elemento de cliente del documento o NULL si no hay más elementos de cliente.

### <a name="remarks"></a>Observaciones

Después de cada llamada, el valor de *pos* se establece para el siguiente elemento del documento, que puede ser o no un elemento de cliente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>COleDocument:: GetNextItem

Llame a esta función varias veces para tener acceso a cada uno de los elementos del documento.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*pos*<br/>
Referencia a un valor de posición establecido por una llamada anterior a `GetNextItem`; la función miembro `GetStartPosition` devuelve el valor inicial.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento de documento situado en la posición especificada.

### <a name="remarks"></a>Observaciones

Después de cada llamada, el valor de *pos* se establece en el valor de posición del siguiente elemento del documento. Si el elemento recuperado es el último elemento del documento, el nuevo valor de *pos* es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>COleDocument:: GetNextServerItem

Llame a esta función varias veces para tener acceso a cada uno de los elementos del servidor del documento.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*pos*<br/>
Referencia a un valor de posición establecido por una llamada anterior a `GetNextServerItem`; la función miembro `GetStartPosition` devuelve el valor inicial.

### <a name="return-value"></a>Valor devuelto

Puntero al siguiente elemento de servidor del documento o NULL si no hay más elementos de servidor.

### <a name="remarks"></a>Observaciones

Después de cada llamada, el valor de *pos* se establece para el siguiente elemento del documento, que puede ser o no un elemento de servidor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>COleDocument:: GetPrimarySelectedItem

Lo llama el marco de trabajo para recuperar el elemento OLE seleccionado actualmente en la vista especificada.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Puntero al objeto de vista activo que muestra el documento.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento OLE único seleccionado; Es NULL si no hay elementos OLE seleccionados o si se ha seleccionado más de uno.

### <a name="remarks"></a>Observaciones

La implementación predeterminada busca en la lista de elementos OLE contenidos para un único elemento seleccionado y devuelve un puntero a él. Si no hay ningún elemento seleccionado, o si hay más de un elemento seleccionado, la función devuelve NULL. Debe invalidar la función miembro `CView::IsSelected` en la clase de vista para que esta función funcione. Invalide esta función si tiene su propio método para almacenar elementos OLE contenidos.

##  <a name="getstartposition"></a>COleDocument:: GetStartPosition

Llame a esta función para obtener la posición del primer elemento del documento.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de posición que se puede usar para empezar a recorrer en iteración los elementos del documento; ES NULL si el documento no tiene ningún elemento.

### <a name="remarks"></a>Observaciones

Pase el valor devuelto a `GetNextItem`, `GetNextClientItem`o `GetNextServerItem`.

##  <a name="hasblankitems"></a>COleDocument:: HasBlankItems

Llame a esta función para determinar si el documento contiene algún elemento en blanco.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento contiene elementos en blanco; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Un elemento en blanco es aquél cuyo rectángulo está vacío.

##  <a name="oneditchangeicon"></a>COleDocument:: OnEditChangeIcon

Muestra el cuadro de diálogo Cambiar icono de OLE y cambia el icono que representa el elemento OLE seleccionado actualmente al icono que el usuario selecciona en el cuadro de diálogo.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Observaciones

`OnEditChangeIcon` crea e inicia un cuadro de diálogo `COleChangeIconDialog` cambiar icono.

##  <a name="oneditconvert"></a>COleDocument:: OnEditConvert

Muestra el cuadro de diálogo convertir OLE y convierte o activa el elemento OLE seleccionado actualmente según las selecciones del usuario en el cuadro de diálogo.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Observaciones

`OnEditConvert` crea e inicia un cuadro de diálogo convertir `COleConvertDialog`.

Un ejemplo de conversión consiste en convertir un documento de Microsoft Word en un documento de WordPad.

##  <a name="oneditlinks"></a>COleDocument:: OnEditLinks

Muestra el cuadro de diálogo Editar/vínculos OLE.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Observaciones

`OnEditLinks` crea e inicia un cuadro de diálogo de vínculos de `COleLinksDialog` que permite al usuario cambiar los objetos vinculados.

##  <a name="onfilesendmail"></a>COleDocument:: OnFileSendMail

Envía un mensaje a través del host de correo residente (si existe) con el documento como datos adjuntos.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Observaciones

`OnFileSendMail` llama `OnSaveDocument` para serializar (guardar) documentos sin título y modificados en un archivo temporal, que se envía a través del correo electrónico. Si el documento no se ha modificado, no es necesario un archivo temporal. se envía el original. `OnFileSendMail` carga MAPI32. DLL si aún no se ha cargado.

A diferencia de la implementación de `OnFileSendMail` para `CDocument`, esta función controla correctamente los archivos compuestos.

Para obtener más información, vea los [temas de MAPI](../../mfc/mapi.md) y la [compatibilidad con MAPI en los artículos de MFC](../../mfc/mapi-support-in-mfc.md) .

##  <a name="onshowviews"></a>COleDocument:: OnShowViews

El marco de trabajo llama a esta función después de que cambie el estado de visibilidad del documento.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parámetros

*bVisible*<br/>
Indica si el documento se ha vuelto visible o invisible.

### <a name="remarks"></a>Observaciones

La versión predeterminada de esta función no hace nada. Reemplácelo si la aplicación debe realizar algún procesamiento especial cuando cambie la visibilidad del documento.

##  <a name="onupdateeditchangeicon"></a>COleDocument:: OnUpdateEditChangeIcon

Lo llama el marco de trabajo para actualizar el comando Cambiar icono en el menú edición.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a una estructura de `CCmdUI` que representa el menú que generó el comando UPDATE. El controlador de actualización llama a la función miembro `Enable` de la estructura `CCmdUI` a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

`OnUpdateEditChangeIcon` actualiza la interfaz de usuario del comando en función de si existe o no un icono válido en el documento. Invalide esta función para cambiar el comportamiento.

##  <a name="onupdateeditlinksmenu"></a>COleDocument:: OnUpdateEditLinksMenu

Lo llama el marco de trabajo para actualizar el comando links en el menú edición.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a una estructura de `CCmdUI` que representa el menú que generó el comando UPDATE. El controlador de actualización llama a la función miembro `Enable` de la estructura `CCmdUI` a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

A partir del primer elemento OLE del documento, `OnUpdateEditLinksMenu` accede a cada elemento, prueba si el elemento es un vínculo y, si es un vínculo, habilita el comando links. Invalide esta función para cambiar el comportamiento.

##  <a name="onupdateobjectverbmenu"></a>COleDocument:: OnUpdateObjectVerbMenu

Lo llama el marco de trabajo para actualizar el comando *objectname* en el menú edición y el submenú Verb al que se tiene acceso desde el comando *objectname* , donde *objectname* es el nombre del objeto OLE incrustado en el documento.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a una estructura de `CCmdUI` que representa el menú que generó el comando UPDATE. El controlador de actualización llama a la función miembro `Enable` de la estructura `CCmdUI` a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

`OnUpdateObjectVerbMenu` actualiza la interfaz de usuario del comando *objectname* en función de si existe o no un objeto válido en el documento. Si existe un objeto, se habilita el comando *objectname* en el menú Editar. Cuando este comando de menú está seleccionado, se muestra el submenú verbo. El submenú verbo contiene todos los comandos de verbo disponibles para el objeto, como editar, propiedades, etc. Invalide esta función para cambiar el comportamiento.

##  <a name="onupdatepastelinkmenu"></a>COleDocument:: OnUpdatePasteLinkMenu

Lo llama el marco de trabajo para determinar si un elemento OLE vinculado se puede pegar desde el portapapeles.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a una estructura de `CCmdUI` que representa el menú que generó el comando UPDATE. El controlador de actualización llama a la función miembro `Enable` de la estructura `CCmdUI` a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

El comando de menú pegar especial está habilitado o deshabilitado dependiendo de si el elemento se puede pegar en el documento o no.

##  <a name="onupdatepastemenu"></a>COleDocument:: OnUpdatePasteMenu

Lo llama el marco de trabajo para determinar si un elemento OLE incrustado se puede pegar desde el portapapeles.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a una estructura de `CCmdUI` que representa el menú que generó el comando UPDATE. El controlador de actualización llama a la función miembro `Enable` de la estructura `CCmdUI` a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

El comando y el botón pegar del menú están habilitados o deshabilitados dependiendo de si el elemento se puede pegar en el documento o no.

##  <a name="removeitem"></a>COleDocument:: RemoveItem

Llame a esta función para quitar un elemento del documento.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento que se va a quitar.

### <a name="remarks"></a>Observaciones

Normalmente no es necesario llamar a esta función explícitamente. lo llaman los destructores para `COleClientItem` y `COleServerItem`.

##  <a name="updatemodifiedflag"></a>COleDocument:: UpdateModifiedFlag

Llame a esta función para marcar el documento como modificado si se ha modificado alguno de los elementos OLE contenidos.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Observaciones

Esto permite al marco de trabajo preguntar al usuario si desea guardar el documento antes de cerrarlo, incluso si los datos nativos del documento no se han modificado.

## <a name="see-also"></a>Consulte también

[CONTENEDOR de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
