---
title: "Limitaciones del enlace de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enlace de datos [C++], limitaciones de Visual C++"
ms.assetid: 376d7738-5252-4caa-adda-a5486ab2a2a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Limitaciones del enlace de datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El enlace de datos constituye una forma eficaz de crear aplicaciones de datos rápidamente.  Sin embargo, la arquitectura actual de los controles de enlace de datos es esencialmente de dos niveles.  
  
## Escalabilidad  
 Los controles enlazados a datos de ADO sólo pueden tener acceso a datos del control de datos ADO.  Los controles enlazados a datos de RDO sólo pueden tener acceso a datos del control RemoteData de RDO.  Para el control RemoteData de RDO no hay otra solución que utilizar una arquitectura de dos niveles, que hace que el servidor de bases de datos reciba directamente todas las solicitudes de recuperación de datos.  Para evitar la conexión directa al servidor de bases de datos, programe un proveedor que permita el acceso a objetos de negocios y de datos de nivel medio.  El control de datos ADO se conecta a estos objetos, en lugar de al servidor de bases de datos.  Estos objetos de nivel medio pueden almacenarse en caché y administrarse en un servidor de transacciones como los servicios de COM\+ 1.0.  
  
## Control de versiones y distribución  
 Cuando se lancen nuevas versiones de los controles, será necesario probar la aplicación con las nuevas versiones.  Si se instala otra aplicación en el equipo de un usuario que tiene versiones diferentes de los controles, será necesario comprobar la aplicación.  Por último, cuando se lancen nuevas versiones de los controles, será necesario distribuir los nuevos controles a los usuarios de la aplicación.  
  
 **Controladores y proveedores**  
  
 El enlace de datos no ofrece más prestaciones que el controlador ODBC o el proveedor OLE DB que está utilizando.  Como los controladores y los proveedores se encargan de exponer datos a los controles de datos, es importante asegurarse de que el controlador o el proveedor admite la funcionalidad que necesita.  Cuando selecciona un controlador o un proveedor, también debe asegurarse de que los usuarios tienen instalado el controlador o el proveedor.  Esto incluye la instalación del software intermedio que requiera el controlador o el proveedor.  Por ejemplo, para obtener conectividad ODBC con Oracle, el usuario debe tener instalado no sólo el controlador ODBC para Oracle, sino también el software intermedio SQL\*Net de Oracle.  Para obtener conectividad con servidores de Oracle 7.3 se recomienda el controlador ODBC para Oracle de Microsoft.  
  
 **Programabilidad**  
  
 Como los controles ActiveX están diseñados como componentes de tipo caja negra, la programabilidad está limitada al acceso de un programador a las interfaces del control.  En el modelo de enlace de datos en el editor de recursos, esto se implementa mediante [clases contenedoras](../../data/ado-rdo/wrapper-classes.md) generadas por el Asistente para insertar controles ActiveX.  Si este asistente no puede detectar una coclase, no se generará ninguna clase contenedora y no habrá acceso mediante programación.  
  
 A pesar de estas limitaciones, el enlace de datos ofrece una forma de crear rápidamente prototipos de aplicaciones de procesamiento de datos mediante Visual C\+\+.  Si la rapidez de desarrollo es importante, debe considerarse el uso del enlace de datos al diseñar la aplicación.  
  
## Vea también  
 [Enlace de datos con controles ActiveX en Visual C\+\+](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)