---
title: DCOMCNFG | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DCOMCNFG
dev_langs: C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bffed7658232d11dd7741900d6eca14de341e855
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="dcomcnfg"></a>DCOMCNFG
**DCOMCNFG** es una utilidad de Windows NT 4.0 que permite configurar diversos valores específicos de DCOM en el registro. El **DCOMCNFG** ventana tiene tres páginas: seguridad predeterminada, propiedades predeterminadas y aplicaciones. En Windows 2000 está presente una cuarta página protocolos predeterminados.  
  
## <a name="default-security-page"></a>Página seguridad predeterminada  
 Puede usar la página de configuración de seguridad predeterminada para especificar permisos predeterminados para objetos en el sistema. La página seguridad predeterminada tiene tres secciones: acceso, inicio y configuración. Para cambiar los valores predeterminados de una sección, haga clic en el correspondiente **editar valores predeterminados** botón. Esta configuración de seguridad predeterminada se almacena en el registro bajo `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.  
  
## <a name="default-protocols-page"></a>Página protocolos predeterminados  
 Esta página enumera el conjunto de protocolos de red disponibles para DCOM en este equipo. El orden refleja la prioridad en el que se van a utilizar; el primer elemento de la lista tiene la prioridad más alta. Protocolos se pueden agregar o eliminar desde esta página.  
  
## <a name="default-properties-page"></a>Página Propiedades predeterminadas  
 En la página de propiedades predeterminadas, debe seleccionar la **Habilitar COM distribuido en este equipo** casilla de verificación si desea que los clientes en otros equipos para objetos de acceso COM que se ejecutan en este equipo. Al seleccionar esta opción establece la `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` valor a `Y`.  
  
## <a name="applications-page"></a>Página de aplicaciones  
 Cambiar la configuración para un objeto determinado con la página de aplicaciones. Simplemente seleccione la aplicación de la lista y haga clic en el **propiedades** botón. La ventana Propiedades tiene cinco páginas:  
  
-   La página General confirma la aplicación que está trabajando.  
  
-   La página ubicación permite especificar dónde se debe ejecutar la aplicación cuando un cliente llama a `CoCreateInstance` en el CLSID relevante. Si selecciona el **ejecutar la aplicación en el siguiente equipo** casilla de verificación y escriba un nombre de equipo, un `RemoteServerName` valor se agrega bajo el AppID de esa aplicación. Borrar el **ejecutar aplicación en este equipo** cambia el nombre de casilla de verificación el `LocalService` valor `_LocalService` y, por lo tanto, lo deshabilita.  
  
-   La página de seguridad es similar a la seguridad predeterminada de página detecta en el **DCOMCNFG** ventana, excepto en que esta configuración se aplica solo a la aplicación actual. Una vez más, la configuración se almacena bajo el AppID de ese objeto.  
  
-   La página identidad identifica el usuario que se utiliza para ejecutar la aplicación.  
  
-   La página extremos enumera el conjunto de protocolos y extremos disponibles para su uso por los clientes del servidor DCOM seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de](../atl/atl-services.md)

