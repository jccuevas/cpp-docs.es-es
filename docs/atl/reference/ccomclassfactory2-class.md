---
title: "CComClassFactory2 Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComClassFactory2<license>"
  - "CComClassFactory2"
  - "ATL.CComClassFactory2<license>"
  - "ATL::CComClassFactory2"
  - "ATL.CComClassFactory2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactory2 class"
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactory2 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa la interfaz de [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) .  
  
## Sintaxis  
  
```  
  
      template <  
   class license  
>  
class CComClassFactory2 : public IClassFactory2,  
   public CComObjectRootEx<CComGlobalsThreadModel>,  
   public license  
```  
  
#### Parámetros  
 *licencia*  
 Una clase que implementa las funciones estáticas siguientes:  
  
-   **static BOOL VerifyLicenseKey\( BSTR**  `bstr`\);  
  
-   **static BOOL GetLicenseKey\( DWORD**  `dwReserved` **, BSTR\***  `pBstr`\);  
  
-   **BOOL estático IsLicenseValid\( \);**  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](../Topic/CComClassFactory2::CreateInstance.md)|crea un objeto de CLSID especificado.|  
|[CComClassFactory2::CreateInstanceLic](../Topic/CComClassFactory2::CreateInstanceLic.md)|Dada una clave de licencia, crea un objeto de CLSID especificado.|  
|[CComClassFactory2::GetLicInfo](../Topic/CComClassFactory2::GetLicInfo.md)|Recupera información que describe las funciones de autorización de generador de clases.|  
|[CComClassFactory2::LockServer](../Topic/CComClassFactory2::LockServer.md)|Bloquea la generador de clases en memoria.|  
|[CComClassFactory2::RequestLicKey](../Topic/CComClassFactory2::RequestLicKey.md)|Crea y devuelve una clave de licencia.|  
  
## Comentarios  
 `CComClassFactory2` implementa la interfaz de [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) , que es una extensión de [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364).  Creación de objetos de los controles de**IClassFactory2** a través de licencias.  Un generador de clases que se ejecuta en un equipo con licencia puede proporcionar una clave de licencia en tiempo de ejecución.  Esta clave de licencia permite que una aplicación para crear instancias de objetos cuando no existe una licencia completa del equipo.  
  
 Objetos ATL adquieren normalmente un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md).  Esta clase incluye [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)macros, que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) mientras el generador predeterminada de la clase.  Para utilizar `CComClassFactory2`, especifique la macro de [DECLARE\_CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) en la definición de clase del objeto.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/CPP/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**, el parámetro de plantilla a `CComClassFactory2`, debe implementar las funciones estáticas `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`.  A continuación se muestra un ejemplo de una clase simple de licencia:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/CPP/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` deriva de ambos **CComClassFactory2Base** y *license*.  **CComClassFactory2Base**, a su vez, se deriva de **IClassFactory2** y de **CComObjectRootEx\< CComGlobalsThreadModel \>**.  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComClassFactoryAutoThread Class](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton Class](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)