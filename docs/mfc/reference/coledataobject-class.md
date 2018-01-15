---
title: Clase COleDataObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
dev_langs: C++
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f85a1e6992e8d679401f4e0f97080efcf991446
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="coledataobject-class"></a>Clase COleDataObject
Se utiliza en las transferencias de datos para recuperar datos en diferentes formatos del Portapapeles, mediante arrastrar y colocar o a partir de un elemento OLE incrustado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDataObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](#coledataobject)|Construye un objeto `COleDataObject`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDataObject::Attach](#attach)|Asocia el objeto de datos OLE especificado en el `COleDataObject`.|  
|[COleDataObject::AttachClipboard](#attachclipboard)|Asocia el objeto de datos que se encuentra en el Portapapeles.|  
|[COleDataObject:: BeginEnumFormats](#beginenumformats)|Se prepara para uno o más posteriormente `GetNextFormat` llamadas.|  
|[COleDataObject::Detach](#detach)|Desasocia asociado `IDataObject` objeto.|  
|[COleDataObject::GetData](#getdata)|Copia datos desde el objeto de datos OLE adjunto en un formato especificado.|  
|[COleDataObject::GetFileData](#getfiledata)|Copia los datos desde el objeto de datos OLE adjunto en un `CFile` puntero en el formato especificado.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Copia los datos desde el objeto de datos OLE adjunto en un `HGLOBAL` en el formato especificado.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Devuelve el siguiente formato de datos disponible.|  
|[COleDataObject:: IsDataAvailable](#isdataavailable)|Comprueba si los datos están disponibles en un formato especificado.|  
|[COleDataObject::Release](#release)|Desasocia y libera asociado `IDataObject` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `COleDataObject`no tiene una clase base.  
  
 Estos tipos de transferencias de datos incluyen un origen y un destino. El origen de datos se implementa como un objeto de la [COleDataSource](../../mfc/reference/coledatasource-class.md) clase. Cada vez que una aplicación de destino tiene datos colocados en él o se solicitará que realice una operación de pegar desde el Portapapeles, un objeto de la `COleDataObject` debe crearse la clase.  
  
 Esta clase le permite determinar si los datos existen en un formato especificado. Puede también enumere los formatos de datos disponibles o comprobar si un formato determinado está disponible y, a continuación, recuperar los datos en el formato preferido. Recuperación de objetos puede realizarse de varias maneras, incluido el uso de un [CFile](../../mfc/reference/cfile-class.md), `HGLOBAL`, o un **STGMEDIUM** estructura.  
  
 Para obtener más información, consulte el [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura en el SDK de Windows.  
  
 Para obtener más información sobre el uso de objetos de datos en la aplicación, vea el artículo [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `COleDataObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="attach"></a>COleDataObject::Attach  
 Llame a esta función para asociar el `COleDataObject` objeto con un objeto de datos OLE.  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpDataObject*  
 Apunta a un objeto de datos OLE.  
  
 `bAutoRelease`  
 **TRUE** si el objeto de datos OLE debe ser liberarla a la `COleDataObject` objetos se destruyen; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) del SDK de Windows.  
  
##  <a name="attachclipboard"></a>COleDataObject::AttachClipboard  
 Llame a esta función para asociar el objeto de datos que se encuentra actualmente en el Portapapeles para la `COleDataObject` objeto.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Llamar a esta función bloquea el Portapapeles hasta que se libere este objeto de datos. Se libera el objeto de datos en el destructor para la `COleDataObject`. Para obtener más información, consulte [llamar a OpenClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649048) y [CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) en la documentación de Win32.  
  
##  <a name="beginenumformats"></a>COleDataObject:: BeginEnumFormats  
 Llame a esta función para prepararse para las llamadas subsiguientes a `GetNextFormat` para recuperar una lista de formatos de datos desde el elemento.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `BeginEnumFormats`, se almacena la posición del primer formato compatible con este objeto de datos. Las llamadas sucesivas a `GetNextFormat` enumerará la lista de formatos disponibles en el objeto de datos.  
  
 Para comprobar la disponibilidad de datos en un formato determinado, utilice [COleDataObject:: IsDataAvailable](#isdataavailable).  
  
 Para obtener más información, consulte [IDataObject:: EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) del SDK de Windows.  
  
##  <a name="coledataobject"></a>COleDataObject::COleDataObject  
 Construye un objeto `COleDataObject`.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Una llamada a [COleDataObject::Attach](#attach) o [COleDataObject::AttachClipboard](#attachclipboard) deben realizarse antes de llamar a otros `COleDataObject` funciones.  
  
> [!NOTE]
>  Dado que uno de los parámetros a los controladores de arrastrar y colocar es un puntero a un `COleDataObject`, no es necesario llamar a este constructor para admitir de arrastrar y colocar.  
  
##  <a name="detach"></a>COleDataObject::Detach  
 Llame a esta función para separar el `COleDataObject` objeto de su objeto de datos OLE asociado sin liberar el objeto de datos.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de datos OLE que se ha separado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdata"></a>COleDataObject::GetData  
 Llame a esta función para recuperar datos desde el elemento en el formato especificado.  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpStgMedium`  
 Apunta a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura que va a recibir datos.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se devolverán datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan los valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) del SDK de Windows.  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) del SDK de Windows.  
  
##  <a name="getfiledata"></a>COleDataObject::GetFileData  
 Llame a esta función para crear un `CFile` o `CFile`-objeto derivado y recuperar datos en el formato especificado en un `CFile` puntero.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se devolverán datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan los valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la nueva `CFile` o `CFile`-objeto derivado que contiene los datos si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Según el medio de los datos se almacenan en el tipo real que señala el valor devuelto puede ser `CFile`, `CSharedFile`, o `COleStreamFile`.  
  
> [!NOTE]
>  La `CFile` objeto tiene acceso con el valor devuelto de esta función es propiedad del autor de la llamada. Es responsabilidad del autor de la llamada a **eliminar** la `CFile` objeto, con lo que se cierre el archivo.  
  
 Para obtener más información, consulte [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) del SDK de Windows.  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) del SDK de Windows.  
  
##  <a name="getglobaldata"></a>COleDataObject::GetGlobalData  
 Llame a esta función para asignar un bloque de memoria global y recuperar datos en el formato especificado en un `HGLOBAL`.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se devolverán datos. Especifique un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan los valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del bloque de memoria global que contiene los datos si se realiza correctamente; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) del SDK de Windows.  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) del SDK de Windows.  
  
##  <a name="getnextformat"></a>COleDataObject::GetNextFormat  
 Llame a esta función repetidamente con el fin de obtener todos los formatos disponibles para recuperar datos desde el elemento.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que recibe la información de formato cuando finaliza la llamada de función.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si otro formato está disponible; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a [COleDataObject:: BeginEnumFormats](#beginenumformats), se almacena la posición del primer formato compatible con este objeto de datos. Las llamadas sucesivas a `GetNextFormat` enumerará la lista de formatos disponibles en el objeto de datos. Use estas funciones para enumerar los formatos disponibles.  
  
 Para comprobar la disponibilidad de un formato determinado, llame a [COleDataObject:: IsDataAvailable](#isdataavailable).  
  
 Para obtener más información, consulte [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) en el SDK de Windows.  
  
##  <a name="isdataavailable"></a>COleDataObject:: IsDataAvailable  
 Llame a esta función para determinar si un formato determinado está disponible para recuperar datos desde el elemento OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato de datos del Portapapeles que se usará en la estructura que señala `lpFormatEtc`. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por las ventanas nativas [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) función.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato deseado. Especifique un valor para este parámetro solo si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por `cfFormat`. Si es **NULL**, se usan los valores predeterminados para el resto de los campos de la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si los datos están disponibles en el formato especificado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función resulta útil antes de llamar a `GetData`, `GetFileData`, o `GetGlobalData`.  
  
 Para obtener más información, consulte [IDataObject:: QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) del SDK de Windows.  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) del SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="release"></a>COleDataObject::Release  
 Llame a esta función para liberar la propiedad de la [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) objeto que estaba asociado previamente a la `COleDataObject` objeto.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Comentarios  
 El `IDataObject` se asoció el `COleDataObject` mediante una llamada a **adjuntar** o `AttachClipboard` o explícitamente por el marco de trabajo. Si el `bAutoRelease` parámetro de **adjuntar** es **FALSE**, la `IDataObject` objeto no se publicará. En este caso, el llamador es responsable de liberar la `IDataObject` mediante una llamada a [IUnknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDataSource (clase)](../../mfc/reference/coledatasource-class.md)   
 [Clase de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
