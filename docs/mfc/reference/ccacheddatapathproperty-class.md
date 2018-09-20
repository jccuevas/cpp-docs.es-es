---
title: CCachedDataPathProperty (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c22d905e50c6811c82ee54d6ec08c57ef3f41182
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382835"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty (clase)

Implementa una propiedad de control OLE transferida de forma asincrónica y almacenada en memoria caché en un archivo de memoria.

## <a name="syntax"></a>Sintaxis

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Construye un objeto `CCachedDataPathProperty`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` objeto en el que los datos en caché.|

## <a name="remarks"></a>Comentarios

Un archivo de memoria se almacena en la memoria RAM en lugar de en disco y es útil para las transferencias de fast temporales.

Junto con `CAysncMonikerFile` y `CDataPathProperty`, `CCachedDataPathProperty` proporciona funcionalidad para el uso de monikers asincrónicos en los controles OLE. Con `CCachedDataPathProperty` objetos, puede transferir datos de forma asincrónica desde un origen de archivo o dirección URL y almacenarla en un archivo de memoria a través de la `m_Cache` variable pública. Todos los datos se almacena en el archivo de memoria y no es necesario invalidar [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) a menos que desee observar las notificaciones y responder. Por ejemplo, si va a transferir un gran tamaño. Archivo GIF y desea notificar a su control que ha llegado más datos y debe actualizarse a sí mismo, invalidar `OnDataAvailable` para realizar la notificación.

La clase `CCachedDataPathProperty` se deriva de `CDataPathProperty`.

Para obtener más información sobre cómo usar controles ActiveX y monikers asincrónicos en aplicaciones de Internet, vea los temas siguientes:

- [Internet primeros pasos: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Internet primeros pasos: Monikers asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)

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

##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty

Construye un objeto `CCachedDataPathProperty`.

```
CCachedDataPathProperty(COleControl* pControl = NULL);


CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
Un puntero al objeto que se asociará con este control ActiveX `CCachedDataPathProperty` objeto.

*lpszPath*<br/>
La ruta de acceso, que puede ser absoluta o relativa, se usa para crear un moniker asincrónico que hace referencia a la ubicación absoluta real de la propiedad. `CCachedDataPathProperty` usa las direcciones URL, no los nombres de archivo. Si desea que un `CCachedDataPathProperty` para un archivo de objeto, anteponga file:// a la ruta de acceso.

### <a name="remarks"></a>Comentarios

El `COleControl` objeto señalado por *pControl* usa [abierto](../../mfc/reference/cdatapathproperty-class.md#open) y recuperados por las clases derivadas. Si *pControl* es NULL, el control usado con `Open` debe establecerse con [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Si *lpszPath* es NULL, puede pasar en la ruta de acceso a través de `Open` o establecerlo con [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache

Contiene el nombre del archivo de memoria en la que se almacena en caché datos de la clase.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Comentarios

Un archivo de memoria se almacena en la memoria RAM en lugar de en disco.

## <a name="see-also"></a>Vea también

[CDataPathProperty (clase)](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty (clase)](../../mfc/reference/cdatapathproperty-class.md)
