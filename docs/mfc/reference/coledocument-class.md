---
title: COleDocument (Clase)
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
ms.openlocfilehash: 1500035cb8be3036678090918154829aace48d2f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753877"
---
# <a name="coledocument-class"></a>COleDocument (Clase)

La clase base para los documentos de OLE que admiten la edición visual.

## <a name="syntax"></a>Sintaxis

```
class COleDocument : public CDocument
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|Construye un objeto `COleDocument`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDocument::AddItem](#additem)|Agrega un elemento a la lista de elementos mantenidos por el documento.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Establece el dispositivo de destino de impresión para todos los elementos de cliente del documento.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Hace que los documentos se almacenen con el formato de archivo de almacenamiento estructurado OLE.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Devuelve el elemento OLE que está activo actualmente en su lugar.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Obtiene el siguiente elemento de cliente para iterar.|
|[COleDocument::GetNextItem](#getnextitem)|Obtiene el siguiente elemento de documento para iterar.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Obtiene el siguiente elemento de servidor para iterar.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Devuelve el elemento OLE seleccionado principal en el documento.|
|[COleDocument::GetStartPosition](#getstartposition)|Obtiene la posición inicial para comenzar la iteración.|
|[COleDocument::HasBlankItems](#hasblankitems)|Comprueba si hay elementos en blanco en el documento.|
|[COleDocument::OnShowViews](#onshowviews)|Se llama cuando el documento se vuelve visible o invisible.|
|[COleDocument::RemoveItem](#removeitem)|Quita un elemento de la lista de elementos mantenidos por el documento.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Marca el documento como modificado si se ha modificado alguno de los elementos OLE contenidos.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Controla los eventos en el comando de menú Cambiar icono.|
|[COleDocument::OnEditConvert](#oneditconvert)|Controla la conversión de un objeto incrustado o vinculado de un tipo a otro.|
|[COleDocument::OnEditLinks](#oneditlinks)|Controla los eventos del comando Vínculos del menú Editar.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo con el documento adjunto.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Llamado por el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Editar/Cambiar icono.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Llamado por el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Editar/Vínculos.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Llamado por el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú *Editar/NombreObjeto* y el submenú Verbo al que se tiene acceso desde *Editar/NombreObjeto*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Llamado por el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Pegar especial.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Llamado por el marco de trabajo para actualizar la interfaz de usuario de comandos para la opción de menú Pegar.|

## <a name="remarks"></a>Observaciones

`COleDocument`se deriva `CDocument`de , lo que permite a las aplicaciones OLE usar la arquitectura de documento/vista proporcionada por la biblioteca Microsoft Foundation Class.

`COleDocument`trata un documento como una colección de [CDocItem](../../mfc/reference/cdocitem-class.md) objetos para controlar los elementos OLE. Tanto las aplicaciones de contenedor como las de servidor requieren una arquitectura de este tipo porque sus documentos deben poder contener elementos OLE. Las clases [COleServerItem](../../mfc/reference/coleserveritem-class.md) y [COleClientItem,](../../mfc/reference/coleclientitem-class.md) ambas derivadas de `CDocItem`, administran las interacciones entre aplicaciones y elementos OLE.

Si está escribiendo una aplicación contenedora `COleDocument`simple, derive la clase de documento de . Si está escribiendo una aplicación contenedora que admite la vinculación a los elementos incrustados contenidos en sus documentos, derive la clase de documento de [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Si está escribiendo una aplicación de servidor o un contenedor/servidor combinado, derive la clase de documento de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc`y `COleServerDoc` se derivan `COleDocument`de , por lo que `COleDocument` `CDocument`estas clases heredan todos los servicios disponibles en y .

Para `COleDocument`usar , derive una clase de ella y agregue funcionalidad para administrar los datos no OLE de la aplicación, así como elementos incrustados o vinculados. Si define `CDocItem`clases derivadas para almacenar los datos nativos de la `COleDocument` aplicación, puede usar la implementación predeterminada definida para almacenar los datos OLE y no OLE. También puede diseñar sus propias estructuras de datos para almacenar los datos no OLE por separado de los elementos OLE. Para obtener más información, consulte el artículo [Contenedores: archivos compuestos](../../mfc/containers-compound-files.md)..

`CDocument`admite el envío de su documento por correo si el soporte de correo (MAPI) está presente. `COleDocument`ha actualizado [OnFileSendMail](#onfilesendmail) para manejar documentos compuestos correctamente. Para obtener más información, vea los artículos Compatibilidad con [MAPI](../../mfc/mapi.md) y [MAPI en MFC](../../mfc/mapi-support-in-mfc.md)..

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coledocumentadditem"></a><a name="additem"></a>COleDocument::AddItem

Llame a esta función para agregar un elemento al documento.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento que se va a agregar.

### <a name="remarks"></a>Observaciones

No es necesario llamar a esta función explícitamente cuando se llama por el `COleClientItem` constructor o `COleServerItem` que acepta un puntero a un documento.

## <a name="coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice

Llame a esta función para cambiar el dispositivo de destino de impresión para todos los elementos [COleClientItem](../../mfc/reference/coleclientitem-class.md) incrustados en el documento contenedor de la aplicación.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parámetros

*Dpt*<br/>
Puntero a `DVTARGETDEVICE` una estructura de datos, que contiene información sobre el nuevo dispositivo de destino de impresión. Puede ser NULL.

*Ppd*<br/>
Puntero a `PRINTDLG` una estructura de datos, que contiene información sobre el nuevo dispositivo de destino de impresión. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función actualiza el dispositivo de destino de impresión para todos los elementos, pero no actualiza la caché de presentación de esos elementos. Para actualizar la caché de presentación de un elemento, llame a [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Los argumentos de esta función contienen información que OLE usa para identificar el dispositivo de destino. La estructura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) contiene información que Windows utiliza para inicializar el cuadro de diálogo Imprimir común. Después de que el usuario cierra el cuadro de diálogo, Windows devuelve información sobre las selecciones del usuario en esta estructura. El `m_pd` miembro de un [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objeto es una `PRINTDLG` estructura.

Para obtener más información, consulte la estructura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) en el Windows SDK.

Para obtener más información, consulte la estructura [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) en el Windows SDK.

## <a name="coledocumentcoledocument"></a><a name="coledocument"></a>COleDocument::COleDocument

Construye un objeto `COleDocument`.

```
COleDocument();
```

## <a name="coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile

Llame a esta función si desea almacenar el documento utilizando el formato de archivo compuesto.

```cpp
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
Especifica si la compatibilidad con archivos compuestos está habilitada o deshabilitada.

### <a name="remarks"></a>Observaciones

Esto también se denomina almacenamiento estructurado. Normalmente se llama a esta `COleDocument`función desde el constructor de la clase derivada. Para obtener más información acerca de los documentos compuestos, vea el artículo [Contenedores: archivos compuestos](../../mfc/containers-compound-files.md)..

Si no llama a esta función miembro, los documentos se almacenarán en un formato de archivo no estructurado ("plano").

Después de habilitar o deshabilitar la compatibilidad con archivos compuestos para un documento, la configuración no se debe cambiar durante la duración del documento.

## <a name="coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem

Llame a esta función para obtener el elemento OLE que está activado actualmente en su lugar en la ventana de marco que contiene la vista identificada por *pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que muestra el documento contenedor.

### <a name="return-value"></a>Valor devuelto

Un puntero al único elemento OLE activo en el lugar; NULL si no hay ningún elemento OLE actualmente en el estado "activo en el lugar".

## <a name="coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COleDocument::GetNextClientItem

Llame a esta función repetidamente para tener acceso a cada uno de los elementos de cliente del documento.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Una referencia a un valor POSITION `GetNextClientItem`establecido por una llamada anterior a ; el valor inicial lo `GetStartPosition` devuelve la función miembro.

### <a name="return-value"></a>Valor devuelto

Un puntero al siguiente elemento de cliente en el documento, o NULL si no hay más elementos de cliente.

### <a name="remarks"></a>Observaciones

Después de cada llamada, el valor de *pos* se establece para el siguiente elemento del documento, que puede ser o no un elemento cliente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

## <a name="coledocumentgetnextitem"></a><a name="getnextitem"></a>COleDocument::GetNextItem

Llame a esta función repetidamente para tener acceso a cada uno de los elementos del documento.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Una referencia a un valor POSITION `GetNextItem`establecido por una llamada anterior a ; el valor inicial lo `GetStartPosition` devuelve la función miembro.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento de documento en la posición especificada.

### <a name="remarks"></a>Observaciones

Después de cada llamada, el valor de *pos* se establece en el valor POSITION del siguiente elemento del documento. Si el elemento recuperado es el último elemento del documento, el nuevo valor de *pos* es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

## <a name="coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COleDocument::GetNextServerItem

Llame a esta función repetidamente para tener acceso a cada uno de los elementos de servidor del documento.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Una referencia a un valor POSITION `GetNextServerItem`establecido por una llamada anterior a ; el valor inicial lo `GetStartPosition` devuelve la función miembro.

### <a name="return-value"></a>Valor devuelto

Un puntero al siguiente elemento de servidor en el documento, o NULL si no hay más elementos de servidor.

### <a name="remarks"></a>Observaciones

Después de cada llamada, el valor de *pos* se establece para el siguiente elemento del documento, que puede ser o no un elemento de servidor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

## <a name="coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem

Llamado por el marco de trabajo para recuperar el elemento OLE seleccionado actualmente en la vista especificada.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Puntero al objeto de vista activo que muestra el documento.

### <a name="return-value"></a>Valor devuelto

Un puntero al único elemento OLE seleccionado; NULL si no se selecciona ningún elemento OLE o si se selecciona más de uno.

### <a name="remarks"></a>Observaciones

La implementación predeterminada busca en la lista de elementos OLE contenidos un único elemento seleccionado y devuelve un puntero a él. Si no hay ningún elemento seleccionado, o si hay más de un elemento seleccionado, la función devuelve NULL. Debe invalidar `CView::IsSelected` la función miembro en la clase de vista para que esta función funcione. Invalide esta función si tiene su propio método de almacenamiento de elementos OLE contenidos.

## <a name="coledocumentgetstartposition"></a><a name="getstartposition"></a>COleDocument::GetStartPosition

Llame a esta función para obtener la posición del primer elemento del documento.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para comenzar a recorrer iteración los elementos del documento; NULL si el documento no tiene elementos.

### <a name="remarks"></a>Observaciones

Pase el valor `GetNextItem` `GetNextClientItem`devuelto `GetNextServerItem`a , , o .

## <a name="coledocumenthasblankitems"></a><a name="hasblankitems"></a>COleDocument::HasBlankItems

Llame a esta función para determinar si el documento contiene elementos en blanco.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento contiene elementos en blanco; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un elemento en blanco es aquel cuyo rectángulo está vacío.

## <a name="coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon

Muestra el cuadro de diálogo Icono de cambio OLE y cambia el icono que representa el elemento OLE seleccionado actualmente al icono que el usuario selecciona en el cuadro de diálogo.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Observaciones

`OnEditChangeIcon`crea e inicia `COleChangeIconDialog` un cuadro de diálogo Cambiar icono.

## <a name="coledocumentoneditconvert"></a><a name="oneditconvert"></a>COleDocument::OnEditConvert

Muestra el cuadro de diálogo Convertir OLE y convierte o activa el elemento OLE seleccionado actualmente según las selecciones de usuario en el cuadro de diálogo.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Observaciones

`OnEditConvert`crea e inicia `COleConvertDialog` un cuadro de diálogo Convertir.

Un ejemplo de conversión es la conversión de un documento de Microsoft Word en un documento de WordPad.

## <a name="coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument::OnEditLinks

Muestra el cuadro de diálogo Edición/Vínculos OLE.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Observaciones

`OnEditLinks`crea e inicia `COleLinksDialog` un cuadro de diálogo Vínculos que permite al usuario cambiar los objetos vinculados.

## <a name="coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COleDocument::OnFileSendMail

Envía un mensaje a través del host de correo residente (si existe) con el documento como archivo adjunto.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Observaciones

`OnFileSendMail`llamadas `OnSaveDocument` para serializar (guardar) documentos sin título y modificados en un archivo temporal, que luego se envía por correo electrónico. Si el documento no se ha modificado, no se necesita un archivo temporal; se envía el original. `OnFileSendMail`carga MAPI32. DLL si aún no se ha cargado.

A diferencia `OnFileSendMail` de `CDocument`la implementación de for , esta función maneja los archivos compuestos correctamente.

Para obtener más información, vea los [temas MAPI](../../mfc/mapi.md) y compatibilidad con MAPI en artículos [de MFC.](../../mfc/mapi-support-in-mfc.md)

## <a name="coledocumentonshowviews"></a><a name="onshowviews"></a>COleDocument::OnShowViews

El marco de trabajo llama a esta función después de que cambie el estado de visibilidad del documento.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parámetros

*bVisible*<br/>
Indica si el documento se ha vuelto visible o invisible.

### <a name="remarks"></a>Observaciones

La versión predeterminada de esta función no hace nada. Invalide si la aplicación debe realizar cualquier procesamiento especial cuando cambie la visibilidad del documento.

## <a name="coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon

Llamado por el marco de trabajo para actualizar el comando Cambiar icono en el menú Editar.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a `CCmdUI` una estructura que representa el menú que generó el comando update. El controlador de `Enable` actualización llama `CCmdUI` a la función miembro de la estructura a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

`OnUpdateEditChangeIcon`actualiza la interfaz de usuario del comando en función de si existe o no un icono válido en el documento. Invalide esta función para cambiar el comportamiento.

## <a name="coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu

Llamado por el marco de trabajo para actualizar el comando Vínculos en el menú Editar.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a `CCmdUI` una estructura que representa el menú que generó el comando update. El controlador de `Enable` actualización llama `CCmdUI` a la función miembro de la estructura a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

A partir del primer elemento `OnUpdateEditLinksMenu` OLE del documento, tiene acceso a cada elemento, comprueba si el elemento es un vínculo y, si es un vínculo, habilita el comando Vínculos. Invalide esta función para cambiar el comportamiento.

## <a name="coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu

Llamado por el marco de trabajo para actualizar el comando *ObjectName* en el menú Edición y el submenú Verbo al que se tiene acceso desde el comando *ObjectName,* donde *ObjectName* es el nombre del objeto OLE incrustado en el documento.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a `CCmdUI` una estructura que representa el menú que generó el comando update. El controlador de `Enable` actualización llama `CCmdUI` a la función miembro de la estructura a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

`OnUpdateObjectVerbMenu`actualiza la interfaz de usuario del comando *ObjectName* en función de si existe o no un objeto válido en el documento. Si existe un objeto, el comando *ObjectName* del menú Editar está habilitado. Cuando se selecciona este comando de menú, se muestra el submenú Verbo. El submenú Verbo contiene todos los comandos de verbo disponibles para el objeto, como Editar, Propiedades, etc. Invalide esta función para cambiar el comportamiento.

## <a name="coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu

Llamado por el marco de trabajo para determinar si un elemento OLE vinculado se puede pegar desde el Portapapeles.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a `CCmdUI` una estructura que representa el menú que generó el comando update. El controlador de `Enable` actualización llama `CCmdUI` a la función miembro de la estructura a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

El comando de menú Pegado especial está activado o deshabilitado en función de si el elemento se puede pegar en el documento o no.

## <a name="coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu

Llamado por el marco de trabajo para determinar si un elemento OLE incrustado se puede pegar desde el Portapapeles.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a `CCmdUI` una estructura que representa el menú que generó el comando update. El controlador de `Enable` actualización llama `CCmdUI` a la función miembro de la estructura a través de *pCmdUI* para actualizar la interfaz de usuario.

### <a name="remarks"></a>Observaciones

El comando y el botón del menú Pegar están habilitados o deshabilitados en función de si el elemento se puede pegar en el documento o no.

## <a name="coledocumentremoveitem"></a><a name="removeitem"></a>COleDocument::RemoveItem

Llame a esta función para quitar un elemento del documento.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento que se va a quitar.

### <a name="remarks"></a>Observaciones

Normalmente no es necesario llamar a esta función explícitamente; es llamado por los `COleClientItem` destructores para y `COleServerItem`.

## <a name="coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COleDocument::UpdateModifiedFlag

Llame a esta función para marcar el documento como modificado si se ha modificado alguno de los elementos OLE contenidos.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Observaciones

Esto permite que el marco de trabajo solicite al usuario que guarde el documento antes de cerrarlo, incluso si los datos nativos del documento no se han modificado.

## <a name="see-also"></a>Vea también

[CONTENEDOR de muestra de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
