---
title: "CAtlServiceModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlServiceModuleT"
  - "ATL.CAtlServiceModuleT"
  - "CAtlServiceModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlServiceModuleT class"
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAtlServiceModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa un servicio.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
UINT nServiceNameID   
>  
class ATL_NO_VTABLE CAtlServiceModuleT :  
public CAtlExeModuleT< T>  
```  
  
#### Parámetros  
 `T`  
 la clase derivada de `CAtlServiceModuleT`.  
  
 *nServiceNameID*  
 El identificador de recurso del servicio.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlServiceModuleT::CAtlServiceModuleT](../Topic/CAtlServiceModuleT::CAtlServiceModuleT.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlServiceModuleT::Handler](../Topic/CAtlServiceModuleT::Handler.md)|La rutina de controlador para el servicio.|  
|[CAtlServiceModuleT::InitializeSecurity](../Topic/CAtlServiceModuleT::InitializeSecurity.md)|Proporciona la configuración de seguridad predeterminada para el servicio.|  
|[CAtlServiceModuleT::Install](../Topic/CAtlServiceModuleT::Install.md)|Las instalaciones y crea el servicio.|  
|[CAtlServiceModuleT::IsInstalled](../Topic/CAtlServiceModuleT::IsInstalled.md)|Confirma que el servicio se ha instalado.|  
|[CAtlServiceModuleT::LogEvent](../Topic/CAtlServiceModuleT::LogEvent.md)|Escribe en el registro de eventos.|  
|[CAtlServiceModuleT::OnContinue](../Topic/CAtlServiceModuleT::OnContinue.md)|Invalide este método para reanudar el servicio.|  
|[CAtlServiceModuleT::OnInterrogate](../Topic/CAtlServiceModuleT::OnInterrogate.md)|Invalide este método para interrogar al servicio.|  
|[CAtlServiceModuleT::OnPause](../Topic/CAtlServiceModuleT::OnPause.md)|invalide este método para pausar el servicio.|  
|[CAtlServiceModuleT::OnShutdown](../Topic/CAtlServiceModuleT::OnShutdown.md)|invalide este método para cerrar el servicio|  
|[CAtlServiceModuleT::OnStop](../Topic/CAtlServiceModuleT::OnStop.md)|invalide este método para detener el servicio|  
|[CAtlServiceModuleT::OnUnknownRequest](../Topic/CAtlServiceModuleT::OnUnknownRequest.md)|Invalide este método para administrar solicitudes desconocidas al servicio|  
|[CAtlServiceModuleT::ParseCommandLine](../Topic/CAtlServiceModuleT::ParseCommandLine.md)|Analiza la línea de comandos y realiza el registro en caso necesario.|  
|[CAtlServiceModuleT::PreMessageLoop](../Topic/CAtlServiceModuleT::PreMessageLoop.md)|Este método se llama inmediatamente antes de escribir el bucle de mensajes.|  
|[CAtlServiceModuleT::RegisterAppId](../Topic/CAtlServiceModuleT::RegisterAppId.md)|registra el servicio en el registro.|  
|[CAtlServiceModuleT::Run](../Topic/CAtlServiceModuleT::Run.md)|Ejecutar el servicio.|  
|[CAtlServiceModuleT::ServiceMain](../Topic/CAtlServiceModuleT::ServiceMain.md)|El método llamado por el administrador de control de servicios.|  
|[CAtlServiceModuleT::SetServiceStatus](../Topic/CAtlServiceModuleT::SetServiceStatus.md)|Actualiza el estado del servicio.|  
|[CAtlServiceModuleT::Start](../Topic/CAtlServiceModuleT::Start.md)|Llamado por `CAtlServiceModuleT::WinMain` al iniciar el servicio.|  
|[CAtlServiceModuleT::Uninstall](../Topic/CAtlServiceModuleT::Uninstall.md)|detiene y quita el servicio.|  
|[CAtlServiceModuleT::Unlock](../Topic/CAtlServiceModuleT::Unlock.md)|Disminuye el recuento de bloqueo del servicio.|  
|[CAtlServiceModuleT::UnregisterAppId](../Topic/CAtlServiceModuleT::UnregisterAppId.md)|Quita el servicio de registro.|  
|[CAtlServiceModuleT::WinMain](../Topic/CAtlServiceModuleT::WinMain.md)|Este método aplica el código necesario para ejecutar el servicio.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlServiceModuleT::m\_bService](../Topic/CAtlServiceModuleT::m_bService.md)|El mensaje que indica el programa se ejecuta como servicio.|  
|[CAtlServiceModuleT::m\_dwThreadID](../Topic/CAtlServiceModuleT::m_dwThreadID.md)|Variable miembro que almacena el identificador del subproceso.|  
|[CAtlServiceModuleT::m\_hServiceStatus](../Topic/CAtlServiceModuleT::m_hServiceStatus.md)|Variable miembro que almacena un identificador a la estructura de información de estado del servicio actual.|  
|[CAtlServiceModuleT::m\_status](../Topic/CAtlServiceModuleT::m_status.md)|Variable miembro que almacena la estructura de información de estado del servicio actual.|  
|[CAtlServiceModuleT::m\_szServiceName](../Topic/CAtlServiceModuleT::m_szServiceName.md)|El nombre del servicio que está registrado.|  
  
## Comentarios  
 `CAtlServiceModuleT`, derivado de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementa un módulo ATL Service.  `CAtlServiceModuleT` proporciona métodos para el procesamiento, la instalación, registrar, y la eliminación de la línea de comandos.  Si se requiere la funcionalidad adicional, éstos y otros métodos pueden reemplazar.  
  
 esta clase reemplaza [clase de CComModule](../../atl/reference/ccommodule-class.md) obsoleto utilizado en versiones anteriores de ATL.  Vea [Clases de módulo ATL](../../atl/atl-module-classes.md) para más detalles.  
  
## Jerarquía de herencia  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)  
  
 `CAtlServiceModuleT`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CAtlExeModuleT Class](../../atl/reference/catlexemodulet-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)