---
title: Clase COleDataSource | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [C++], MFC support
- Clipboard [C++], OLE support
- uniform data transfer
- OLE [C++], uniform data transfer
- Clipboard [C++], MFC support
- OLE Clipboard [C++], support
- IDataObject, MFC encapsulation
- data transfer [C++], OLE
- COleDataSource class
- OLE data transfer [C++]
- uniform data transfer, OLE
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 3839ebe5f278d71f933b6e76f2ad50dc8e62a165
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="coledatasource-class"></a>COleDataSource (clase)
Actúa como una memoria caché donde una aplicación coloca los datos que proporcionará durante las operaciones de transferencia de datos, tales como las operaciones del Portapapeles y de arrastrar y colocar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](#coledatasource)|Construye un objeto `COleDataSource`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[:: CacheData](#cachedata)|Proporciona datos en un formato especificado mediante un **STGMEDIUM** estructura.|  
|[COleDataSource:: CacheGlobalData](#cacheglobaldata)|Proporciona datos en un formato especificado mediante un `HGLOBAL`.|  
|[COleDataSource:: DelayRenderData](#delayrenderdata)|Proporciona datos en un formato especificado mediante la representación aplazada.|  
|[COleDataSource:: DelayRenderFileData](#delayrenderfiledata)|Proporciona datos en un formato especificado en un `CFile` puntero.|  
|[COleDataSource::DelaySetData](#delaysetdata)|Llamado para todos los formatos que se admiten en `OnSetData`.|  
|[COleDataSource:: DoDragDrop](#dodragdrop)|Realiza operaciones de arrastrar y colocar con un origen de datos.|  
|[COleDataSource::Empty](#empty)|Vacía la `COleDataSource` objeto de datos.|  
|[COleDataSource::FlushClipboard](#flushclipboard)|Representa todos los datos en el Portapapeles.|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Comprueba que los datos que se colocan en el Portapapeles sean estando allí.|  
|[COleDataSource::OnRenderData](#onrenderdata)|Recupera los datos como parte de la representación aplazada.|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Recupera los datos en un `CFile` como parte de la representación aplazada.|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Recupera los datos en un `HGLOBAL` como parte de la representación aplazada.|  
|[COleDataSource::OnSetData](#onsetdata)|Se invoca para reemplazar los datos de la `COleDataSource` objeto.|  
|[COleDataSource:: SetClipboard](#setclipboard)|Coloca un `COleDataSource` objeto en el Portapapeles.|  
  
## <a name="remarks"></a>Comentarios  
 Puede crear orígenes de datos OLE directamente. Como alternativa, el [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md) clases crean orígenes de datos OLE en respuesta a sus `CopyToClipboard` y `DoDragDrop` funciones miembro. Vea [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) para obtener una breve descripción. Invalidar el `OnGetClipboardData` función miembro de la clase de elemento del elemento o servidor de cliente para agregar formatos de Portapapeles adicionales a los datos en el origen de datos OLE creado para la `CopyToClipboard` o `DoDragDrop` función miembro.  
  
 Siempre que desee para preparar los datos para una transferencia, debe crear un objeto de esta clase y rellenarlo con los datos mediante el método más adecuado para los datos. La forma en se inserta en un origen de datos se ve directamente afectada por si los datos se suministran inmediatamente (procesamiento inmediato) o a petición (procesamiento aplazado). Para cada formato de Portapapeles en el que va a proporcionar datos pasando el formato del Portapapeles que se usará (y opcional [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura), llame a [DelayRenderData](#delayrenderdata).  
  
 Para obtener más información acerca de los orígenes de datos y transferencia de datos, vea el artículo [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Además, el artículo [Portapapeles temas](../../mfc/clipboard.md) describe el mecanismo del Portapapeles de OLE.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="cachedata"></a>:: CacheData  
 Llame a esta función para especificar un formato en el que datos se ofrezcan las operaciones de transferencia de datos.  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato de Portapapeles en el que se pueden ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpStgMedium`  
 Apunta a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura que contiene los datos en el formato especificado.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se pueden ofrecer los datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="remarks"></a>Comentarios  
 Debe proporcionar los datos, ya que esta función proporciona mediante el uso de la representación inmediata. Los datos se almacena en caché hasta que sea necesario.  
  
 Proporcione los datos mediante un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura. También puede usar el `CacheGlobalData` función de miembro si la cantidad de datos que está proporcionando es lo suficientemente pequeño como para transferir eficazmente mediante un `HGLOBAL`.  
  
 Después de llamar a `CacheData` el **ptd** miembro de `lpFormatEtc` y el contenido de `lpStgMedium` son propiedad del objeto de datos, no por el llamador.  
  
 Para utilizar la representación aplazada, llame a la [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para obtener más información, consulte el [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) las estructuras de los [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="cacheglobaldata"></a>COleDataSource:: CacheGlobalData  
 Llame a esta función para especificar un formato en el que datos se ofrezcan las operaciones de transferencia de datos.  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato de Portapapeles en el que se pueden ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 *hGlobal*  
 Identificador de bloque de memoria global que contiene los datos en el formato especificado.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se pueden ofrecer los datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="remarks"></a>Comentarios  
 Esta función proporciona los datos mediante la representación de inmediato, por lo que debe suministrar los datos cuando se llama a la función; los datos se almacena en caché hasta que sea necesario. Use la `CacheData` función de miembro si se proporciona una gran cantidad de datos o si necesita un medio de almacenamiento estructurado.  
  
 Para utilizar la representación aplazada, llame a la [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para obtener más información, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="coledatasource"></a>COleDataSource::COleDataSource  
 Construye un objeto `COleDataSource`.  
  
```  
COleDataSource();
```  
  
##  <a name="delayrenderdata"></a>COleDataSource:: DelayRenderData  
 Llame a esta función para especificar un formato en el que datos se ofrezcan las operaciones de transferencia de datos.  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato de Portapapeles en el que se pueden ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se pueden ofrecer los datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="remarks"></a>Comentarios  
 Esta función proporciona los datos mediante la representación diferida, por lo que los datos no se suministran inmediatamente. El [OnRenderData](#onrenderdata) o [OnRenderGlobalData](#onrenderglobaldata) función miembro se llama para solicitar los datos.  
  
 Use esta función si no va a proporcionar los datos a través de un `CFile` objeto. Si va a proporcionar los datos a través de un `CFile` objeto, llame a la [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para usar la representación inmediata, llame a la [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) función miembro.  
  
 Para obtener más información, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="delayrenderfiledata"></a>COleDataSource:: DelayRenderFileData  
 Llame a esta función para especificar un formato en el que datos se ofrezcan las operaciones de transferencia de datos.  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato de Portapapeles en el que se pueden ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se pueden ofrecer los datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="remarks"></a>Comentarios  
 Esta función proporciona los datos mediante la representación diferida, por lo que los datos no se suministran inmediatamente. El [OnRenderFileData](#onrenderfiledata) función miembro se llama para solicitar los datos.  
  
 Use esta función si va a utilizar un `CFile` objeto que se va a proporcionar los datos. Si no va a usar un `CFile` objeto, llame a la [DelayRenderData](#delayrenderdata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para usar la representación inmediata, llame a la [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) función miembro.  
  
 Para obtener más información, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="delaysetdata"></a>COleDataSource::DelaySetData  
 Llame a esta función para admitir el cambio del contenido del origen de datos.  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato de Portapapeles en el que se colocarán los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se reemplazarán los datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="remarks"></a>Comentarios  
 [OnSetData](#onsetdata) llamará el marco de trabajo cuando esto ocurre. Solo se utiliza cuando el marco de trabajo devuelve el origen de datos de [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Si `DelaySetData` no se llama a su `OnSetData` función nunca se llamará. `DelaySetData`se debe llamar para cada Portapapeles o **FORMATETC** compatibilidad con el formato.  
  
 Para obtener más información, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="dodragdrop"></a>COleDataSource:: DoDragDrop  
 Llame a la `DoDragDrop` función de miembro para realizar una operación de arrastrar y colocar para este origen de datos, normalmente en un [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) controlador.  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwEffects`  
 Operaciones de arrastrar y colocar permitidas en este origen de datos. Puede tener uno o varios de los siguientes:  
  
- `DROPEFFECT_COPY`Se pudo realizar una operación de copia.  
  
- `DROPEFFECT_MOVE`Se pudo realizar una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo de los datos perdidos a los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que podría producirse una operación de desplazamiento de arrastre.  
  
 `lpRectStartDrag`  
 Puntero al rectángulo que define donde realmente comienza la operación de arrastre. Para obtener más información, vea la sección Comentarios que se muestra más adelante.  
  
 *pDropSource*  
 Apunta a un origen de colocación. Si **NULL** , a continuación, una implementación predeterminada de [COleDropSource](../../mfc/reference/coledropsource-class.md) se usará.  
  
### <a name="return-value"></a>Valor devuelto  
 Quitar efecto generado por la operación de arrastrar y colocar; en caso contrario `DROPEFFECT_NONE` si nunca se comienza la operación porque el usuario suelta el botón del mouse antes de abandonar el rectángulo proporcionado.  
  
### <a name="remarks"></a>Comentarios  
 No se inicie inmediatamente la operación de arrastrar y colocar. Espera hasta que el cursor del mouse deja el rectángulo especificado por `lpRectStartDrag` o hasta que un número especificado de milisegundos transcurridos. Si `lpRectStartDrag` es **NULL**, el tamaño del rectángulo es un píxel.  
  
 El tiempo de retraso especificado por un valor de una clave del registro. Puede cambiar el tiempo de retraso mediante una llamada a [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retardo, se utiliza un valor predeterminado de 200 milisegundos. Tiempo de retardo de arrastre se almacena como sigue:  
  
-   Tiempo de retardo de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Tiempo de retardo de arrastre de Windows 3.x se almacena en el archivo WIN. Archivo INI, en la [sección Windows}.  
  
-   Tiempo de retardo de arrastre de Windows 95 ó 98 se almacena en una versión en caché de WIN. INI.  
  
 Para obtener más información acerca de cómo arrastrar información de retraso se almacena en el registro o la. El archivo INI, consulte [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, vea el artículo [arrastrar y colocar: implementar un origen de Drop](../../mfc/drag-and-drop-implementing-a-drop-source.md).  
  
##  <a name="empty"></a>COleDataSource::Empty  
 Llame a esta función para vaciar el `COleDataSource` objeto de datos.  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>Comentarios  
 Ambos se almacenan en caché y formatos de representación de retraso se vacían por lo que se puede volver a usar.  
  
 Para obtener más información, consulte [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="flushclipboard"></a>COleDataSource::FlushClipboard  
 Representa los datos que se encuentra en el Portapapeles y, a continuación, le permite pegar datos del Portapapeles después de cerrar la aplicación.  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>Comentarios  
 Use [SetClipboard](#setclipboard) colocar datos en el Portapapeles.  
  
##  <a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner  
 Determina si los datos en el Portapapeles ha cambiado desde [SetClipboard](#setclipboard) se llame por última vez y, si es así, identifica al propietario actual.  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El origen de datos actualmente en el Portapapeles, o **NULL** si no hay nada en el Portapapeles o si el Portapapeles no pertenece a la aplicación que realiza la llamada.  
  
##  <a name="onrenderdata"></a>COleDataSource::OnRenderData  
 Lo llama el marco de trabajo para recuperar datos en el formato especificado.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `lpStgMedium`  
 Apunta a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura en la que los datos se va a devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una establecidas anteriormente en el `COleDataSource` objeto mediante la [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función de miembro para la representación aplazada. La implementación predeterminada de esta función llamará [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata) si el medio de almacenamiento proporcionado es un archivo o la memoria, respectivamente. Si no se proporciona ninguno de estos formatos, la implementación predeterminada se devuelven 0 y no hacen nada. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Si `lpStgMedium` ->  *tymed* es **TYMED_NULL**, **STGMEDIUM** debe ser asignado y rellenado según lo especificado por *lpFormatEtc-> tymed*. Si no lo es **TYMED_NULL**, **STGMEDIUM** debe rellenarse en lugar de con los datos.  
  
 Avanzada reemplazable. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede que desee invalidar una de las otras versiones de esta función en su lugar. Si los datos son pequeños y un tamaño fijo, invalidar `OnRenderGlobalData`. Si los datos en un archivo, o es de tamaño variable, invalidar `OnRenderFileData`.  
  
 Para obtener más información, consulte el [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructuras, la [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) tipo de enumeración, y [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData  
 Lo llama el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento especificado es un archivo.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `pFile`  
 Apunta a un [CFile](../../mfc/reference/cfile-class.md) objeto en el que se va a representar los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una establecidas anteriormente en el `COleDataSource` objeto mediante la [DelayRenderData](#delayrenderdata) función de miembro para la representación aplazada. La implementación predeterminada de esta función devuelve simplemente **FALSE**.  
  
 Avanzada reemplazable. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos en un archivo, o es de tamaño variable, invalidar `OnRenderFileData`. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para obtener más información, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura y [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData  
 Lo llama el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento especificado es una memoria global.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `phGlobal`  
 Apunta a un identificador de memoria global en el que los datos son va a devolver. Si uno todavía no se ha asignado, este parámetro puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una establecidas anteriormente en el `COleDataSource` objeto mediante la [DelayRenderData](#delayrenderdata) función de miembro para la representación aplazada. La implementación predeterminada de esta función devuelve simplemente **FALSE**.  
  
 Si `phGlobal` es **NULL**, a continuación, un nuevo `HGLOBAL` debe asignar y se devuelve en `phGlobal`. En caso contrario, el `HGLOBAL` especificado por `phGlobal` debe rellenarse con los datos. La cantidad de datos se coloca en el `HGLOBAL` no debe superar el tamaño actual del bloque de memoria. Además, el bloque no se pueden reasignar a un tamaño mayor.  
  
 Avanzada reemplazable. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede que desee invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos en un archivo, o es de tamaño variable, invalidar [OnRenderFileData](#onrenderfiledata). Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para obtener más información, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura y [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onsetdata"></a>COleDataSource::OnSetData  
 Lo llama el marco para establecer o reemplazar los datos de la `COleDataSource` objeto en el formato especificado.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se va a reemplazar datos.  
  
 `lpStgMedium`  
 Apunta a la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura que contiene los datos que va a reemplazar el contenido actual de la `COleDataSource` objeto.  
  
 `bRelease`  
 Indica que tiene una propiedad del medio de almacenamiento después de completar la llamada de función. El llamador decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. El llamador para ello, establezca `bRelease`. Si `bRelease` es distinto de cero, el origen de datos toma la propiedad, el medio que libera cuando termina de usarla. Cuando `bRelease` es 0, el llamador conserva la propiedad y el origen de datos puede utilizar el medio de almacenamiento durante la llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El origen de datos no tomar posesión de los datos hasta que obtuvo correctamente. Es decir, no tienen la propiedad si `OnSetData` devuelve 0. Si el origen de datos toma posesión, libera el medio de almacenamiento mediante una llamada a la [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) función.  
  
 La implementación predeterminada no hace nada. Reemplace esta función para reemplazar los datos en el formato especificado. Avanzada reemplazable.  
  
 Para obtener más información, consulte el [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructuras y los [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) y [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) las funciones en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setclipboard"></a>COleDataSource:: SetClipboard  
 Coloca los datos contenidos en el `COleDataSource` objeto en el Portapapeles después de llamar a una de las siguientes funciones: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), o [DelayRenderFileData](#delayrenderfiledata).  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDataObject (clase)](../../mfc/reference/coledataobject-class.md)

