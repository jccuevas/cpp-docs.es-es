---
title: Clase de CCachedDataPathProperty | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- CCachedDataPathProperty class
- OLE controls [C++], asynchronous
- asynchronous controls [C++]
- memory files [C++]
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6e3f54e6429456be24cbe18471abd1705bbe0034
ms.lasthandoff: 02/24/2017

---
# <a name="ccacheddatapathproperty-class"></a>Clase de CCachedDataPathProperty
Implementa una propiedad de control OLE transferida de forma asincrónica y almacenada en memoria caché en un archivo de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Construye un objeto `CCachedDataPathProperty`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`objeto en el que los datos en caché.|  
  
## <a name="remarks"></a>Comentarios  
 Un archivo de memoria se almacena en RAM, en lugar de en disco y es útil para las transferencias temporales rápido.  
  
 Junto con **CAysncMonikerFile** y `CDataPathProperty`, `CCachedDataPathProperty` proporciona funcionalidad para el uso de monikers asincrónicos en controles OLE. Con `CCachedDataPathProperty` objetos, puede transferir datos desde un origen de archivo o dirección URL de forma asincrónica y almacenarla en un archivo de memoria mediante la `m_Cache` variable pública. Todos los datos se almacenan en el archivo de memoria y no es necesario reemplazar [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) a menos que desee ver las notificaciones y responder. Por ejemplo, si va a transferir de gran tamaño. Archivo GIF y desea notificar el control que ha llegado más datos y debe volver a dibujar, reemplazar `OnDataAvailable` para realizar la notificación.  
  
 La clase `CCachedDataPathProperty` se deriva de `CDataPathProperty`.  
  
 Para obtener más información acerca de cómo utilizar controles ActiveX y monikers asincrónicos en aplicaciones de Internet, vea los temas siguientes:  
  
- [Primeros pasos de Internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Primeros pasos de Internet: Monikers asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty  
 Construye un objeto `CCachedDataPathProperty`.  
  
```  
CCachedDataPathProperty(COleControl* pControl = NULL);

 
CCachedDataPathProperty(
    LPCTSTR lpszPath,  
    COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pControl`  
 Un puntero al objeto de control ActiveX que se asociará con este `CCachedDataPathProperty` objeto.  
  
 `lpszPath`  
 La ruta de acceso, que puede ser absoluta o relativa, se utiliza para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CCachedDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea un `CCachedDataPathProperty` para un archivo de objeto, anteponga file:// a la ruta de acceso.  
  
### <a name="remarks"></a>Comentarios  
 El `COleControl` objeto señalado por `pControl` utiliza [abiertos](../../mfc/reference/cdatapathproperty-class.md#open) y recuperar las clases derivadas. Si `pControl` es **NULL**, el control se utiliza con **abiertos** debe establecerse con [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Si `lpszPath` es **NULL**, puede pasar la ruta de acceso a través de **abiertos** o se establece con [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).  
  
##  <a name="m_cache"></a>CCachedDataPathProperty::m_Cache  
 Contiene el nombre de clase del archivo de memoria en la que se almacena en caché datos.  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un archivo de memoria se almacena en RAM, en lugar de en disco.  
  
## <a name="see-also"></a>Vea también  
 [Clase CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

