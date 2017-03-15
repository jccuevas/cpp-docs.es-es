---
title: Clase COleDataObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDataObject
- COleDataObject
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [C++], MFC support
- Clipboard [C++], OLE support
- uniform data transfer
- OLE [C++], uniform data transfer
- Clipboard [C++], MFC support
- OLE Clipboard [C++], support
- IDataObject interface, MFC encapsulation
- data transfer [C++]
- data transfer [C++], OLE
- OLE data transfer [C++]
- COleDataObject class
- uniform data transfer, OLE
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f30ca208252fe81f1e47d9e8f817cb9137656540
ms.lasthandoff: 02/24/2017

---
# <a name="coledataobject-class"></a>Clase COleDataObject
Se utiliza en las transferencias de datos para recuperar datos en diferentes formatos del Portapapeles, mediante arrastrar y colocar o a partir de un elemento OLE incrustado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDataObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](#coledataobject)|Construye un objeto `COleDataObject`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDataObject::Attach](#attach)|Adjunta el objeto de datos OLE especificado en el `COleDataObject`.|  
|[COleDataObject::AttachClipboard](#attachclipboard)|Asocia el objeto de datos en el Portapapeles.|  
|[COleDataObject:: BeginEnumFormats](#beginenumformats)|Se prepara para uno o más subsiguiente `GetNextFormat` llamadas.|  
|[COleDataObject::Detach](#detach)|Desasocia asociado `IDataObject` objeto.|  
|[COleDataObject::GetData](#getdata)|Copia datos desde el objeto de datos OLE adjunto en un formato especificado.|  
|[COleDataObject::GetFileData](#getfiledata)|Copia datos desde el objeto de datos OLE adjunto en un `CFile` puntero en el formato especificado.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Copia datos desde el objeto de datos OLE adjunto en un `HGLOBAL` en el formato especificado.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Devuelve el siguiente formato de datos disponible.|  
|[COleDataObject:: IsDataAvailable](#isdataavailable)|Comprueba si los datos están disponibles en un formato especificado.|  
|[COleDataObject::Release](#release)|Desasocia y libera asociado `IDataObject` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `COleDataObject`no tiene una clase base.  
  
 Estos tipos de transferencias de datos incluyen un origen y un destino. El origen de datos se implementa como un objeto de la [COleDataSource](../../mfc/reference/coledatasource-class.md) clase. Cada vez que una aplicación de destino tiene datos colocados en él o se le pide que realice una operación de pegar desde el Portapapeles, un objeto de la `COleDataObject` debe crearse la clase.  
  
 Esta clase le permite determinar si los datos existen en un formato especificado. Puede también enumere los formatos de datos disponibles o compruebe si un formato determinado está disponible y, a continuación, recuperar los datos en el formato preferido. Se puede realizar la recuperación de objetos de diferentes maneras, incluido el uso de un [CFile](../../mfc/reference/cfile-class.md), un `HGLOBAL`, o un **STGMEDIUM** estructura.  
  
 Para obtener más información, consulte el [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información acerca de cómo utilizar objetos de datos en su aplicación, vea el artículo [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `COleDataObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="a-nameattacha--coledataobjectattach"></a><a name="attach"></a>COleDataObject::Attach  
 Llame a esta función para asociar el `COleDataObject` con un objeto de datos OLE.  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpDataObject*  
 Apunta a un objeto de datos OLE.  
  
 `bAutoRelease`  
 **TRUE** si el objeto de datos OLE debe ser liberarla al `COleDataObject` objetos se destruyen; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameattachclipboarda--coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject::AttachClipboard  
 Llame a esta función para asociar el objeto de datos que está actualmente en el Portapapeles para el `COleDataObject` objeto.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Llamar a esta función bloquea el Portapapeles hasta que se publique este objeto de datos. Se libera el objeto de datos en el destructor de la `COleDataObject`. Para obtener más información, consulte [llamar a OpenClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649048) y [CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) en la documentación de Win32.  
  
##  <a name="a-namebeginenumformatsa--coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject:: BeginEnumFormats  
 Llame a esta función para prepararse para las llamadas subsiguientes a `GetNextFormat` para recuperar una lista de formatos de datos del elemento.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `BeginEnumFormats`, se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas a `GetNextFormat` se enumere los formatos disponibles en el objeto de datos.  
  
 Para comprobar la disponibilidad de los datos en un formato determinado, utilice [COleDataObject:: IsDataAvailable](#isdataavailable).  
  
 Para obtener más información, consulte [IDataObject:: EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namecoledataobjecta--coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject::COleDataObject  
 Construye un objeto `COleDataObject`.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Una llamada a [COleDataObject::Attach](#attach) o [COleDataObject::AttachClipboard](#attachclipboard) deben realizarse antes de llamar a otros `COleDataObject` funciones.  
  
> [!NOTE]
>  Dado que uno de los parámetros a los controladores de arrastrar y colocar es un puntero a un `COleDataObject`, no es necesario llamar a este constructor para admitir de arrastrar y colocar.  
  
##  <a name="a-namedetacha--coledataobjectdetach"></a><a name="detach"></a>COleDataObject::Detach  
 Llame a esta función para separar el `COleDataObject` objeto de su objeto de datos OLE asociado sin liberar el objeto de datos.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de datos OLE que se separó.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdataa--coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject::GetData  
 Llame a esta función para recuperar datos desde el elemento en el formato especificado.  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (función).  
  
 `lpStgMedium`  
 Apunta a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura que recibirá los datos.  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se devolverán datos. Especifique un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por `cfFormat`. Si es **NULL**, se utilizan los valores predeterminados para los demás campos en la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetfiledataa--coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject::GetFileData  
 Llame a esta función para crear un `CFile` o `CFile`-objeto derivado y recuperar datos en el formato especificado en un `CFile` puntero.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (función).  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se devolverán datos. Especifique un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por `cfFormat`. Si es **NULL**, se utilizan los valores predeterminados para los demás campos en la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la nueva `CFile` o `CFile`-objeto derivado que contiene los datos si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Según el medio de los datos se almacenan en el tipo real señalado por el valor devuelto puede ser `CFile`, `CSharedFile`, o `COleStreamFile`.  
  
> [!NOTE]
>  La `CFile` objeto accediendo el valor devuelto de esta función es propiedad de la llamada. Es responsabilidad del autor de la llamada a **eliminar** la `CFile` objeto, con lo que se cierre el archivo.  
  
 Para obtener más información, consulte [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetglobaldataa--coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject::GetGlobalData  
 Llame a esta función para asignar un bloque de memoria global y recuperar datos en el formato especificado en un `HGLOBAL`.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (función).  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato en el que se devolverán datos. Especifique un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por `cfFormat`. Si es **NULL**, se utilizan los valores predeterminados para los demás campos en la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del bloque de memoria global que contiene los datos si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetnextformata--coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject::GetNextFormat  
 Llame a esta función repetidamente para obtener todos los formatos disponibles para recuperar datos de elemento.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que recibe la información de formato cuando finaliza la llamada de función.  
  
### <a name="return-value"></a>Valor devuelto  
 El formato es distinto de cero si el otro está disponible; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a [COleDataObject:: BeginEnumFormats](#beginenumformats), se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas a `GetNextFormat` se enumere los formatos disponibles en el objeto de datos. Utilice estas funciones para enumerar los formatos disponibles.  
  
 Para comprobar la disponibilidad de un formato determinado, llame a [COleDataObject:: IsDataAvailable](#isdataavailable).  
  
 Para obtener más información, consulte [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameisdataavailablea--coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject:: IsDataAvailable  
 Llame a esta función para determinar si un formato concreto está disponible para recuperar datos de elemento OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cfFormat`  
 El formato de datos de Portapapeles para utilizarlo en la estructura que apunta `lpFormatEtc`. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (función).  
  
 `lpFormatEtc`  
 Apunta a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que describe el formato deseado. Proporcione un valor para este parámetro solo si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por `cfFormat`. Si es **NULL**, se utilizan los valores predeterminados para los demás campos en la **FORMATETC** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si los datos están disponibles en el formato especificado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función resulta útil antes de llamar a `GetData`, `GetFileData`, o `GetGlobalData`.  
  
 Para obtener más información, consulte [IDataObject:: QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="a-namereleasea--coledataobjectrelease"></a><a name="release"></a>COleDataObject::Release  
 Llame a esta función para liberar la propiedad de la [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) objeto que estaba asociado previamente a la `COleDataObject` objeto.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Comentarios  
 El `IDataObject` estuvo asociado a la `COleDataObject` llamando a **adjuntar** o `AttachClipboard` o explícitamente por el marco de trabajo. Si el `bAutoRelease` parámetro de **adjuntar** es **FALSE**, el `IDataObject` no se liberará el objeto. En este caso, el llamador es responsable de liberar la `IDataObject` llamando a [IUnknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [COleDataSource (clase)](../../mfc/reference/coledatasource-class.md)   
 [Clase de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Clase COleServerItem](../../mfc/reference/coleserveritem-class.md)

