---
title: COleTemplateServer (clase)
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: 561da5060aae3c938dc3e55d0310718a881c1a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753729"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer (clase)

Se utiliza para servidores de edición visual OLE, servidores de automatización y contenedores de vínculos (aplicaciones que admiten vínculos con incrustaciones).

## <a name="syntax"></a>Sintaxis

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Construye un objeto `COleTemplateServer`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Conecta una plantilla de `COleObjectFactory` documento al objeto subyacente.|
|[COleTemplateServer::Unregister](#unregister)|Anula el registro de la plantilla de documento asociada.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Registra el tipo de documento con el registro del sistema OLE.|

## <a name="remarks"></a>Observaciones

Esta clase se deriva de la clase [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); por lo general, se puede utilizar `COleTemplateServer` directamente en lugar de derivar su propia clase. `COleTemplateServer`utiliza un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para administrar los documentos del servidor. Utilícelo `COleTemplateServer` al implementar un servidor completo, es decir, un servidor que se puede ejecutar como una aplicación independiente. Los servidores completos suelen ser varias aplicaciones de interfaz de documentos (MDI), aunque se admiten aplicaciones de interfaz de documento único (SDI). Se `COleTemplateServer` necesita un objeto para cada tipo de documento de servidor que admite una aplicación; es decir, si la aplicación de servidor admite hojas `COleTemplateServer` de cálculo y gráficos, debe tener dos objetos.

`COleTemplateServer`invalida `OnCreateInstance` la función `COleObjectFactory`miembro definida por . El marco de trabajo llama a esta función miembro para crear un objeto C++ del tipo adecuado.

Para obtener más información acerca de los servidores, vea el artículo [Servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer

Construye un objeto `COleTemplateServer`.

```
COleTemplateServer();
```

### <a name="remarks"></a>Observaciones

Para obtener una breve descripción del uso de la `COleTemplateServer` clase, consulte el resumen de la clase [COleLinkingDoc.](../../mfc/reference/colelinkingdoc-class.md)

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate

Conecta la plantilla de documento a la que apunta *pDocTemplate* al objeto [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) subyacente.

```cpp
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
Referencia al identificador de clase OLE que solicita la plantilla.

*pDocTemplate*<br/>
Puntero a la plantilla de documento.

*bMultiInstance*<br/>
Indica si una sola instancia de la aplicación puede admitir varias instancias. Si es TRUE, se inician varias instancias de la aplicación para cada solicitud para crear un objeto.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

## <a name="coletemplateserverunregister"></a><a name="unregister"></a>COleTemplateServer::Unregister

Anula el registro de la plantilla de documento asociada.

```
BOOL Unregister();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

EnterRemarks

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a>COleTemplateServer::UpdateRegistry

Carga información de tipo de archivo de la cadena de plantilla de documento y coloca esa información en el registro del sistema OLE.

```cpp
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parámetros

*nAppType*<br/>
Un valor de la OLE_APPTYPE enumeración, que se define en AFXDISP. H. Puede tener cualquiera de los siguientes valores:

- OAT_INPLACE_SERVER Server tiene una interfaz de usuario de servidor completa.

- OAT_SERVER Server solo admite la inserción.

- OAT_CONTAINER Container admite vínculos a objetos incrustados.

- OAT_DISPATCH_OBJECT Objeto `IDispatch`es -capaz.

- OAT_DOC_OBJECT_SERVER Server admite la incrustación y el modelo de componentes de objeto de documento.

*rglpszRegister*<br/>
Una lista de entradas que se escribe en el registro sólo si no existen entradas.

*rglpszOverwrite*<br/>
Una lista de entradas que se escribe en el registro independientemente de si existen entradas anteriores.

*bRegistro*<br/>
Determina si se va a registrar la clase. Si *bRegister* es TRUE, la clase se registra en el registro del sistema. De lo contrario, anula el registro de la clase.

### <a name="remarks"></a>Observaciones

La información de registro se carga mediante una llamada a [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Las subcadenas recuperadas son las `regFileTypeId`identificadas por los índices , `regFileTypeName`, y `fileNewName`, como se describe en las `GetDocString` páginas de referencia.

Si `regFileTypeId` la subcadena está vacía `GetDocString` o si se produce un error en la llamada por cualquier otro motivo, se produce un error en esta función y la información del archivo no se especifica en el registro.

La información de los argumentos *rglpszRegister* y *rglpszOverwrite* se escribe en el registro mediante una llamada a [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). La información predeterminada, que se registra cuando los dos argumentos son NULL, es adecuada para la mayoría de las aplicaciones. Para obtener información sobre la estructura de `AfxOleRegisterServerClass`la información de estos argumentos, consulte .

Para obtener más información, consulta [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory (clase)](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
