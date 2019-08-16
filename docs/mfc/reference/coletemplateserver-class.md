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
ms.openlocfilehash: 4a1997497f3bddb405b712b5534f76e577dabfa8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503095"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer (clase)

Se utiliza para servidores de edición visual OLE, servidores de automatización y contenedores de vínculos (aplicaciones que admiten vínculos con incrustaciones).

## <a name="syntax"></a>Sintaxis

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Construye un objeto `COleTemplateServer`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Conecta una plantilla de documento al objeto `COleObjectFactory` subyacente.|
|[COleTemplateServer::Unregister](#unregister)|Anula el registro de la plantilla de documento asociada.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Registra el tipo de documento en el registro del sistema OLE.|

## <a name="remarks"></a>Comentarios

Esta clase se deriva de la clase [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); Normalmente, puede usar `COleTemplateServer` directamente en lugar de derivar su propia clase. `COleTemplateServer`utiliza un objeto [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) para administrar los documentos de servidor. Se `COleTemplateServer` usa al implementar un servidor completo, es decir, un servidor que se puede ejecutar como una aplicación independiente. Los servidores completos suelen ser aplicaciones de interfaz de múltiples documentos (MDI), aunque se admiten aplicaciones de interfaz de un único documento (SDI). Se `COleTemplateServer` necesita un objeto para cada tipo de documento de servidor que admita una aplicación; es decir, si la aplicación de servidor admite hojas de cálculo y gráficos, debe `COleTemplateServer` tener dos objetos.

`COleTemplateServer`invalida la `OnCreateInstance` función miembro definida por `COleObjectFactory`. El marco de trabajo llama a esta función miembro para crear C++ un objeto del tipo adecuado.

Para obtener más información acerca de los servidores, [consulte el artículo servidores: Implementar un servidor](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="coletemplateserver"></a>  COleTemplateServer::COleTemplateServer

Construye un objeto `COleTemplateServer`.

```
COleTemplateServer();
```

### <a name="remarks"></a>Comentarios

Para obtener una breve descripción del uso de la `COleTemplateServer` clase, vea la información general sobre la clase [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) .

##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate

Conecta la plantilla de documento a la que apunta *pDocTemplate* al objeto [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) subyacente.

```
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
Indica si una única instancia de la aplicación puede admitir varias creaciones de instancias. Si es TRUE, se inician varias instancias de la aplicación para cada solicitud de creación de un objeto.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte la [clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

##  <a name="unregister"></a>  COleTemplateServer::Unregister

Anula el registro de la plantilla de documento asociada.

```
BOOL Unregister();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

EnterRemarks

##  <a name="updateregistry"></a>  COleTemplateServer::UpdateRegistry

Carga la información de tipo de archivo de la cadena de plantilla de documento y coloca esa información en el registro del sistema OLE.

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parámetros

*nAppType*<br/>
Un valor de la enumeración OLE_APPTYPE, que se define en AFXDISP. C. Puede tener cualquiera de los siguientes valores:

- El servidor de OAT_INPLACE_SERVER tiene una interfaz de usuario de servidor completa.

- El servidor OAT_SERVER solo admite la inserción.

- El contenedor OAT_CONTAINER admite vínculos a objetos incrustados.

- El objeto OAT_DISPATCH_OBJECT `IDispatch`es compatible.

- El servidor OAT_DOC_OBJECT_SERVER admite la inserción y el modelo de componentes de objeto de documento.

*rglpszRegister*<br/>
Una lista de entradas que se escriben en el registro solo si no existe ninguna entrada.

*rglpszOverwrite*<br/>
Una lista de entradas que se escriben en el registro independientemente de si existen entradas anteriores.

*bRegister*<br/>
Determina si la clase se va a registrar. Si *bRegister* es true, la clase se registra con el registro del sistema. De lo contrario, anula el registro de la clase.

### <a name="remarks"></a>Comentarios

La información de registro se carga por medio de una llamada a [CDocTemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Las subcadenas recuperadas son las identificadas por los `regFileTypeId`índices `regFileTypeName`, y `fileNewName`, tal y como se `GetDocString` describe en las páginas de referencia.

Si la `regFileTypeId` subcadena está vacía o si se produce un `GetDocString` error en la llamada a por cualquier otra razón, se produce un error en esta función y no se especifica la información de archivo en el registro.

La información de los argumentos *rglpszRegister* y *rglpszOverwrite* se escribe en el registro a través de una llamada a [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). La información predeterminada, que se registra cuando los dos argumentos son NULL, es adecuada para la mayoría de las aplicaciones. Para obtener información sobre la estructura de la información de estos argumentos, `AfxOleRegisterServerClass`vea.

Para obtener más información, consulta [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory (clase)](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc (clase)](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
