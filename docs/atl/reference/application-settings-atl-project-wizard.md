---
title: Asistente para proyectos de configuración de la aplicación, ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.atl.com.appset
dev_langs:
- C++
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49e25fa8a730ea31caf747d07ce30a0622c4bd01
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714693"
---
# <a name="application-settings-atl-project-wizard"></a>Configuración de la aplicación, Asistente para proyectos ATL

Use la **configuración de la aplicación** página del Asistente para proyectos ATL para diseñar y agregar características básicas a un nuevo proyecto ATL.

## <a name="server-type"></a>Tipo de servidor

Elija uno de los tres tipos de servidor:

- **Biblioteca de vínculos dinámicos (DLL)**  

   Seleccione esta opción para crear un servidor en proceso.

- **Archivo ejecutable (EXE)**  

   Seleccione esta opción para crear un servidor fuera de proceso local. Esta opción no permite la compatibilidad con MFC ni COM + 1.0. No se permite para la combinación de código auxiliar y proxy.

- **Servicio (EXE)**  

   Seleccione esta opción para crear una aplicación de Windows que se ejecuta en segundo plano cuando se inicia Windows. Esta opción no permite la compatibilidad con MFC ni COM + 1.0 o no se admite para la combinación de código auxiliar y proxy.

## <a name="additional-options"></a>Opciones adicionales

> [!NOTE]
> Todas las opciones adicionales están disponibles para proyectos de archivos DLL solo.

- **Permitir la combinación de código auxiliar y proxy**  

   Seleccione el **permitir la combinación de código auxiliar y proxy** casilla de verificación por comodidad cuando se requiere la serialización de interfaces. Esta opción coloca el código proxy y código auxiliar generado por MIDL en el mismo archivo ejecutable como el servidor.

- **Compatibilidad con MFC**  

   Seleccione esta opción para especificar que el objeto que incluye compatibilidad con MFC. Esta opción vincula el proyecto a las bibliotecas MFC para que puede tener acceso a cualquiera de las clases y funciones que contienen.

- **Compatibilidad con COM + 1.0**  

   Seleccione esta opción para modificar la configuración de compilación del proyecto para admitir los componentes de COM + 1.0. Además de la lista estándar de bibliotecas, el asistente agrega la biblioteca específicos del componente de COM + 1.0 Comsvcs.lib.

   Además, el mtxex.dll es el retraso que se cargan en el sistema host cuando se inicia la aplicación.

- **Registro de componentes de soporte técnico**

   Si el proyecto ATL contiene compatibilidad para los componentes de COM + 1.0, puede establecer esta opción. El registrador de componentes permite al objeto COM + 1.0 obtener una lista de componentes, registrar componentes o anular el registro de componentes (individualmente o a la vez).

## <a name="see-also"></a>Vea también

[Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
[Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)   
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

