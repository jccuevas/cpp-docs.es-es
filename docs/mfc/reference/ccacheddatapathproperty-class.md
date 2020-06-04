---
title: Clase CCachedDataPathProperty
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: ebab34433f23b119e3444b3eaa8b0ad6313555af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352366"
---
# <a name="ccacheddatapathproperty-class"></a>Clase CCachedDataPathProperty

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
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`objeto en el que almacenar datos en caché.|

## <a name="remarks"></a>Observaciones

Un archivo de memoria se almacena en RAM en lugar de en el disco y es útil para transferencias temporales rápidas.

Junto `CAysncMonikerFile` con `CDataPathProperty` `CCachedDataPathProperty` y , proporciona funcionalidad para el uso de monikers asincrónicos en controles OLE. Con `CCachedDataPathProperty` los objetos, puede transferir datos de forma asincrónica desde una dirección `m_Cache` URL o un origen de archivos y almacenarlos en un archivo de memoria a través de la variable pública. Todos los datos se almacenan en el archivo de memoria y no es necesario invalidar [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) a menos que desee buscar notificaciones y responder. Por ejemplo, si está transfiriendo un archivo . GIF y desea notificar a su control que han llegado más `OnDataAvailable` datos y debe volver a dibujarse a sí mismo, invalidar para realizar la notificación.

La `CCachedDataPathProperty` clase se `CDataPathProperty`deriva de .

Para obtener más información acerca de cómo utilizar monikers asincrónicos y controles ActiveX en aplicaciones de Internet, consulte los temas siguientes:

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

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty

Construye un objeto `CCachedDataPathProperty`.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
Puntero al objeto de control ActiveX `CCachedDataPathProperty` que se va a asociar a este objeto.

*lpszPath*<br/>
La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CCachedDataPathProperty`utiliza direcciones URL, no nombres de archivo. Si desea `CCachedDataPathProperty` un objeto para un archivo, anteponga file:// a la ruta de acceso.

### <a name="remarks"></a>Observaciones

El `COleControl` objeto señalado por *pControl* es utilizado por [Open](../../mfc/reference/cdatapathproperty-class.md#open) y recuperado por las clases derivadas. Si *pControl* es NULL, `Open` el control utilizado con debe establecerse con [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Si *lpszPath* es NULL, puede pasar `Open` la ruta de acceso o establecerla con [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a>CCachedDataPathProperty::m_Cache

Contiene el nombre de clase del archivo de memoria en el que se almacenan en caché los datos.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Observaciones

Un archivo de memoria se almacena en RAM en lugar de en el disco.

## <a name="see-also"></a>Consulte también

[Clase CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
