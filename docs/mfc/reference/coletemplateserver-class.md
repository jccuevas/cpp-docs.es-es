---
title: Clase COleTemplateServer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- Automation servers [C++], implementing
- servers, OLE
- OLE server applications, managing server documents
- link containers [C++]
- visual editing, servers
- OLE link containers
- COleTemplateServer class
- OLE server applications, COleTemplateServer class
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ea82939cd0e8a8ba5612c65d238be8ae9996ef08
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Se conecta a una plantilla de documento para subyacente `COleObjectFactory` objeto.|  
|[COleTemplateServer::Unregister](#unregister)|Anula el registro de la plantilla de documento asociado.|  
|[COleTemplateServer:: UpdateRegistry](#updateregistry)|Registra el tipo de documento con el registro del sistema OLE.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se deriva de la clase [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); normalmente, puede usar `COleTemplateServer` directamente en lugar de derivar su propia clase. `COleTemplateServer`utiliza un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para administrar los documentos de servidor. Use `COleTemplateServer` al implementar un servidor completo, es decir, un servidor que se puede ejecutar como una aplicación independiente. Servidores completos suelen ser aplicaciones de múltiples documentos (MDI) de la interfaz, aunque se admiten aplicaciones de único documento (SDI) de la interfaz. Una `COleTemplateServer` objeto necesario para cada tipo de documento de servidor que admite una aplicación; es decir, si la aplicación de servidor es compatible con las hojas de cálculo y gráficos, debe tener dos `COleTemplateServer` objetos.  
  
 `COleTemplateServer`reemplaza el `OnCreateInstance` función de miembro definida por `COleObjectFactory`. Esta función miembro es llamada por el marco para crear un objeto de C++ del tipo correcto.  
  
 Para obtener más información acerca de los servidores, vea el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer  
 Construye un objeto `COleTemplateServer`.  
  
```  
COleTemplateServer();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una breve descripción del uso de la `COleTemplateServer` de clases, consulte la [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) general sobre la clase.  
  
##  <a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate  
 Conecta la plantilla de documento señalada `pDocTemplate` a subyacente [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) objeto.  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 Referencia al identificador de clase OLE que solicita la plantilla.  
  
 `pDocTemplate`  
 Puntero a la plantilla de documento.  
  
 `bMultiInstance`  
 Indica si una sola instancia de la aplicación puede admitir varias creaciones de instancias. Si **TRUE**, se ejecutan varias instancias de la aplicación para que cada solicitud crear un objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="unregister"></a>COleTemplateServer::Unregister  
 Anula el registro de la plantilla de documento asociado.  
  
```  
BOOL Unregister();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 EnterRemarks  
  
##  <a name="updateregistry"></a>COleTemplateServer:: UpdateRegistry  
 Carga la información de tipo de archivo de la cadena de plantilla de documento y coloca dicha información en el registro del sistema OLE.  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nAppType`  
 Un valor de la **OLE_APPTYPE** enumeración, que se define en AFXDISP. H. Puede tener uno de los siguientes valores:  
  
- `OAT_INPLACE_SERVER`Servidor tiene interfaz de usuario de servidor completo.  
  
- `OAT_SERVER`Servidor admite únicamente la incrustación.  
  
- `OAT_CONTAINER`Contenedor admite vínculos a objetos incrustados.  
  
- `OAT_DISPATCH_OBJECT`Objeto es `IDispatch`-capaz.  
  
- **OAT_DOC_OBJECT_SERVER** Server admite tanto la incrustación y el modelo de objeto de documento de componentes.  
  
 `rglpszRegister`  
 Una lista de entradas que se escribe en el registro sólo si no existen entradas.  
  
 `rglpszOverwrite`  
 Una lista de entradas que se escribe en el registro, independientemente de que existan las entradas anteriores.  
  
 `bRegister`  
 Determina si la clase se va a registrar. Si `bRegister` es **TRUE**, la clase se registra con el registro del sistema. De lo contrario, anula el registro de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Se carga la información de registro mediante una llamada a [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Las subcadenas recuperadas son aquéllos identificados por los índices **regFileTypeId**, **regFileTypeName**, y **fileNewName**, como se describe en el `GetDocString` páginas de referencia.  
  
 Si el **regFileTypeId** subcadena está vacía o si la llamada a `GetDocString` se produce un error por cualquier otra razón, esta función produce un error y no se especifica la información de archivo en el registro.  
  
 La información de los argumentos `rglpszRegister` y `rglpszOverwrite` se escribe en el registro mediante una llamada a [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). La información de forma predeterminada, que se registra cuando los dos argumentos son **NULL**, es adecuado para la mayoría de las aplicaciones. Para obtener información sobre la estructura de la información de estos argumentos, vea `AfxOleRegisterServerClass`.  
  
 Para obtener más información, consulte [implementa la interfaz IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [COleObjectFactory (clase)](../../mfc/reference/coleobjectfactory-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleServerDoc](../../mfc/reference/coleserverdoc-class.md)   
 [Clase COleServerItem](../../mfc/reference/coleserveritem-class.md)

