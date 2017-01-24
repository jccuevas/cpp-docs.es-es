---
title: "Utilizar el enlace de datos de RDO en Visual C++ | Microsoft Docs"
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
  - "enlace de datos [C++], RDO"
  - "RDO [C++], enlace de datos"
  - "RemoteData (control de RDO), enlazar datos en Visual C++"
  - "RemoteData (control), enlazar datos en Visual C++"
ms.assetid: 02b9cfe7-7bbe-4a01-b075-e28d9536ac4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar el enlace de datos de RDO en Visual C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para utilizar el enlace de datos de RDO en Visual C\+\+, tiene que agregar un control RemoteData de RDO y apuntar a un origen de datos y un origen de registros \(consulta SQL\).  También debe agregar un control enlazado a datos de RDO, apuntar al mismo desde un control RemoteData de RDO y seleccionar los campos que desea enlazar al origen de registros del control RemoteData de RDO.  
  
### Para utilizar el enlace de datos de RDO en Visual C\+\+  
  
1.  Configure un [origen de datos ODBC](../../data/ado-rdo/odbc-connections.md), si no lo ha hecho ya.  
  
2.  Cree una aplicación de cuadro de diálogo MFC o una aplicación de vista de formulario de MFC mediante el Asistente para aplicaciones MFC.  
  
3.  Agregue el control Microsoft RemoteData \(control RemoteData de RDO\) al cuadro de diálogo; vea [Insertar el control en una aplicación de Visual C\+\+](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md).  
  
4.  Apunte el control RemoteData de RDO al origen de datos ODBC.  
  
    1.  Haga clic en el control con el botón secundario del mouse y, a continuación, haga clic en **Propiedades**.  
  
    2.  Haga clic en la ficha **Control**.  
  
    3.  Establezca como valor de **DataSource** el origen de datos ODBC.  
  
    4.  Si es necesario, establezca el nombre de usuario y la contraseña del origen de datos ODBC.  Déjelos en blanco si el origen de datos no requiere un nombre de usuario y una contraseña.  
  
    5.  Escriba una consulta SQL en la propiedad **SQL**.  Los controles enlazados a datos pueden enlazarse a los resultados de esta consulta.  
  
5.  Establezca las propiedades del control RemoteData de RDO que desee.  
  
6.  Agregue un control enlazado a datos.  Por ejemplo, agregue el **Control DBGrid** y establezca el origen de datos de la manera siguiente.  
  
    1.  Haga clic en DBGrid con el botón secundario del mouse y, a continuación, haga clic en **Propiedades**.  
  
    2.  Haga clic en la ficha **Todas**.  
  
    3.  Establezca como valor de la propiedad **DataSource** un control RemoteData de RDO.  Haga clic en el cuadro combinado desplegable para la propiedad y busque el identificador del control RemoteData de RDO.  El nombre de identificador predeterminado es IDC\_REMOTEDATACTL1.  
  
7.  Para ejecutar en modo de prueba, use CTRL\+T.  Puede desplazarse por los datos.  Presione la tecla ESC o cierre el cuadro de diálogo para finalizar el modo de prueba.  
  
 Si compila y ejecuta el programa, también se puede desplazar por los datos.  
  
## Vea también  
 [Enlace de datos de RDO](../../data/ado-rdo/rdo-databinding.md)   
 [Enlace de datos con controles ActiveX en Visual C\+\+](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)