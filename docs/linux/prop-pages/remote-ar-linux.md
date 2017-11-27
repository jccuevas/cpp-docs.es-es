---
title: Propiedades de archivo remoto (C++ para Linux) | Microsoft Docs
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.Ar.CreateIndex
- VC.Project.Ar.CreateThinArchive
- VC.Project.Ar.NoWarnOnCreate
- VC.Project.Ar.TruncateTimestamp
- VC.Project.Ar.SuppressStartupBanner
- VC.Project.Ar.Verbose
- vc.project.AdditionalOptionsPage
- VC.Project.Ar.OutputFile
- VC.Project.VCConfiguration.BuildLogFile
ms.openlocfilehash: 402fa1f752b311014c828027e45a92a3dc6a2917
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="remote-archive-properties-c-linux"></a>Propiedades de archivo remoto (C++ para Linux)

Propiedad | Descripción
--- | ---
Crear un índice del archivo | Crear un índice de archivo (cf. ranlib).  Esto puede acelerar la vinculación y reducir la dependencia en su propia biblioteca.
Crear archivo fino | Crear un archivo fino.  Un archivo fino contiene las rutas de acceso relativas a los objetos, en lugar de insertar los objetos.  Para cambiar entre Fino y Normal es necesario eliminar la biblioteca existente.
Sin advertencia al crear | No mostrar advertencias cuando se cree la biblioteca.
Truncar marca de tiempo | Usar cero para marcas de tiempo e identificadores UID/GUID.
Suprimir la pancarta de inicio | No mostrar número de versión.
Detallado | Detallado
Opciones adicionales | Opciones adicionales.
Archivo de salida | La opción /OUT invalida el nombre y la ubicación predeterminados del programa que crea lib.
Archivador | Especifica el programa que debe invocarse durante la vinculación de objetos estáticos, o bien la ruta de acceso al archivador en el sistema remoto.
Tiempo de espera del archivador | Tiempo de espera del archivador remoto, en milisegundos.
Copiar salida | Especifica si debe copiarse en la máquina local el archivo de salida de compilación del sistema remoto.
