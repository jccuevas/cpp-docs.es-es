---
title: COleTemplateServer (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
dev_langs:
- C++
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 424d98236b37dabe1c671a9890f049063a8e50a1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212281"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer (clase)
Se utiliza para servidores de edición visual OLE, servidores de automatización y contenedores de vínculos (aplicaciones que admiten vínculos con incrustaciones).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Construye un objeto `COleTemplateServer`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Se conecta a una plantilla de documento subyacente `COleObjectFactory` objeto.|  
|[COleTemplateServer::Unregister](#unregister)|Anula el registro de la plantilla de documento asociado.|  
|[COleTemplateServer:: UpdateRegistry](#updateregistry)|Registra el tipo de documento con el registro del sistema OLE.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se deriva de la clase [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); por lo general, puede usar `COleTemplateServer` directamente en lugar de derivar su propia clase. `COleTemplateServer` usa un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para administrar los documentos de servidor. Use `COleTemplateServer` al implementar un servidor completo, es decir, un servidor que se puede ejecutar como una aplicación independiente. Servidores completos suelen ser aplicaciones de múltiples documentos (MDI) de la interfaz, aunque se admiten las aplicaciones de único documento (SDI) de la interfaz. Una `COleTemplateServer` objeto necesario para cada tipo de documento de servidor compatibles con la aplicación; es decir, si la aplicación de servidor es compatible con las hojas de cálculo y gráficos, debe tener dos `COleTemplateServer` objetos.  
  
 `COleTemplateServer` invalida el `OnCreateInstance` función de miembro definida por `COleObjectFactory`. Esta función miembro se llama el marco de trabajo para crear un objeto de C++ del tipo correcto.  
  
 Para obtener más información acerca de los servidores, consulte el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).  
  
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
 Para obtener una breve descripción del uso de la `COleTemplateServer` de clases, vea el [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) información general de clases.  
  
##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate  
 Se conecta a la que señala a la plantilla de documento *pDocTemplate* subyacente [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) objeto.  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>Parámetros  
 *CLSID*  
 Referencia al identificador de clase OLE que solicita la plantilla.  
  
 *pDocTemplate*  
 Puntero a la plantilla de documento.  
  
 *bMultiInstance al*  
 Indica si una sola instancia de la aplicación puede admitir varias creaciones de instancias. Si es TRUE, se inician múltiples instancias de la aplicación para que cada solicitud crear un objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [clave CLSID](/windows/desktop/com/clsid-key-hklm) en el SDK de Windows.  
  
##  <a name="unregister"></a>  COleTemplateServer::Unregister  
 Anula el registro de la plantilla de documento asociado.  
  
```  
BOOL Unregister();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 EnterRemarks  
  
##  <a name="updateregistry"></a>  COleTemplateServer:: UpdateRegistry  
 Carga información de tipo de archivo de la cadena de plantilla de documento y coloca dicha información en el registro del sistema OLE.  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *nAppType*  
 Un valor de la enumeración OLE_APPTYPE, que se define en AFXDISP. H. Puede tener uno de los siguientes valores:  
  
- OAT_INPLACE_SERVER Server tiene interfaz de usuario de servidor completo.  
  
- OAT_SERVER Server admite solo la incrustación de objetos.  
  
- OAT_CONTAINER contenedor es compatible con vínculos a objetos incrustados.  
  
- Objeto OAT_DISPATCH_OBJECT es `IDispatch`-capaz.  
  
- Servidor OAT_DOC_OBJECT_SERVER admite tanto la incrustación y el modelo de objeto de documento de componentes.  
  
 *rglpszRegister*  
 Una lista de entradas que se escribe en el registro solo si hay entradas.  
  
 *rglpszOverwrite*  
 Una lista de entradas que se escribe en el registro, independientemente de que existan las entradas anteriores.  
  
 *bInscríbase al*  
 Determina si la clase es que se registrarán. Si *bInscríbase al* es TRUE, la clase se registra con el registro del sistema. En caso contrario, anula el registro de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Se carga la información de registro mediante una llamada a [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Las subcadenas que se recuperan las identificadas por los índices son `regFileTypeId`, `regFileTypeName`, y `fileNewName`, tal y como se describe en el `GetDocString` páginas de referencia.  
  
 Si el `regFileTypeId` subcadena está vacía o si la llamada a `GetDocString` se produce un error por cualquier otra razón, esta función se produce un error y no se especifica la información de archivo en el registro.  
  
 La información de los argumentos *rglpszRegister* y *rglpszOverwrite* se escribe en el registro mediante una llamada a [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). La información de forma predeterminada, que se registra cuando los dos argumentos son NULL, es adecuada para la mayoría de las aplicaciones. Para obtener información sobre la estructura de la información de estos argumentos, vea `AfxOleRegisterServerClass`.  
  
 Para obtener más información, consulte [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [COleObjectFactory (clase)](../../mfc/reference/coleobjectfactory-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleServerDoc (clase)](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
