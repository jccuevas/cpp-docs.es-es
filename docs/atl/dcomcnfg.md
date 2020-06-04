---
title: DCOMCNFG
ms.date: 11/04/2016
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
ms.openlocfilehash: a389a46cd02b40cef46d687743fd3416cc4f3154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250789"
---
# <a name="dcomcnfg"></a>DCOMCNFG

DCOMCNFG es una utilidad de Windows NT 4.0 que le permite configurar diversos valores específicos de DCOM en el registro. La ventana DCOMCNFG tiene tres páginas: Seguridad predeterminada, las propiedades predeterminadas y las aplicaciones. En Windows 2000 una cuarta página, protocolos predeterminados, está presente.

## <a name="default-security-page"></a>Página seguridad predeterminada

Puede usar la página de seguridad predeterminada para especificar los permisos predeterminados para los objetos en el sistema. La página de seguridad predeterminada tiene tres secciones: Acceso, inicio y configuración. Para cambiar los valores predeterminados de una sección, haga clic en el correspondiente **editar valores predeterminados** botón. Esta configuración de seguridad predeterminada se almacena en el registro bajo `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.

## <a name="default-protocols-page"></a>Página protocolos predeterminados

Esta página enumera el conjunto de protocolos de red disponibles para DCOM en este equipo. El orden refleja la prioridad en el que se van a utilizar; el primer elemento de la lista tiene la prioridad más alta. Protocolos se pueden agregar o eliminar desde esta página.

## <a name="default-properties-page"></a>Página de propiedades predeterminada

En la página de propiedades predeterminadas, debe seleccionar la **Habilitar COM distribuido en este equipo** casilla de verificación si desea que los clientes en otros equipos a los objetos de acceso COM que se ejecutan en esta máquina. Seleccione esta opción establece la `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` valor `Y`.

## <a name="applications-page"></a>Página aplicaciones

Cambiar la configuración de un objeto determinado con la página de aplicaciones. Simplemente seleccione la aplicación en la lista y haga clic en el **propiedades** botón. La ventana de propiedades tiene cinco páginas:

- La página General confirma la aplicación que está trabajando.

- La página ubicación permite especificar dónde se debe ejecutar la aplicación cuando un cliente llama a `CoCreateInstance` en el CLSID relevante. Si selecciona el **ejecutar la aplicación en el siguiente equipo** casilla de verificación y escriba un nombre de equipo, un `RemoteServerName` valor se agrega bajo el AppID de esa aplicación. Borrar el **ejecutar la aplicación en este equipo** cambia el nombre de casilla de verificación el `LocalService` valor `_LocalService` y, por lo tanto, se deshabilita.

- La página de seguridad es similar a la página de seguridad predeterminada que se encuentra en la ventana DCOMCNFG, salvo que esta configuración se aplica solo a la aplicación actual. De nuevo, la configuración se almacena bajo el AppID de ese objeto.

- La página identidad identifica el usuario que se utiliza para ejecutar la aplicación.

- La página extremos enumera el conjunto de protocolos y extremos disponibles para su uso por los clientes del servidor DCOM seleccionado.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)
