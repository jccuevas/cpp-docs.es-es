---
title: Propiedades de archivo remoto (C++ para Linux) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
author: mikeblome
ms.author: mblome
f1_keywords: []
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 004e015b7e5ad8a99b3bea2bf21b7b598f2fedbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="remote-archive-properties-c-linux"></a>Propiedades de archivo remoto (C++ para Linux)

Property | Description
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
