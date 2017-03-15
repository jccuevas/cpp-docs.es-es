---
title: "Probar propiedades y eventos con un contenedor de prueba | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedor de pruebas de controles ActiveX"
  - "controles ActiveX [C++], pruebas"
  - "depurar controles ActiveX"
  - "propiedades [MFC], pruebas"
  - "contenedor de prueba"
  - "pruebas, contenedores de prueba"
  - "tstcon32.exe"
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Probar propiedades y eventos con un contenedor de prueba
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La aplicación contenedor de prueba, incluida en Visual C\+\+, es un contenedor de controles ActiveX para probar y depurar controles ActiveX.  El contenedor de pruebas permite que el programador de controles probar la funcionalidad del control cambiando sus propiedades, al invocar los métodos, y desencadena sus eventos.  El contenedor de prueba puede mostrar registros de notificaciones de enlace de datos y también proporciona los medios para una funcionalidad de persistencia del control ActiveX de prueba: puede guardar propiedades en una secuencia o el substorage, recargarlas, y examinar los datos almacenados de la secuencia.  En esta sección se describe cómo utilizar las características básicas del contenedor de prueba.  Para obtener información adicional, seleccione el menú de **Ay&uda** mientras se ejecuta el contenedor de prueba.  
  
### Para tener acceso al ActiveX control test container  
  
1.  Compile [Ejemplo TSTCON: ActiveX Control Test Container](../top/visual-cpp-samples.md).  
  
### Para probar el control ActiveX  
  
1.  En el menú de **edición** del contenedor de prueba, haga clic en **Insert New Control**.  
  
2.  En el cuadro de **Insertar control** , seleccione el control que desee y haga clic en **Aceptar**.  El control aparecerá en el contenedor del control.  
  
    > [!NOTE]
    >  Si el control no aparece en el cuadro de diálogo de **Insertar control** , asegúrese de que registradolo con el comando de **Registrar controles** de menú de **archivo** del contenedor de prueba.  
  
 En este punto puede probar las propiedades o los eventos de control.  
  
#### Para probar propiedades  
  
1.  En el menú de **Control** , haga clic en **Invoke Methods**.  
  
2.  En la lista desplegable de **Nombre del método** , seleccione el método de PropPut para la propiedad que desea probar.  
  
3.  Modifique **Valor del parámetro** o **Tipo de parámetro** y haga clic en el botón de **Establecer valor** .  
  
4.  Haga clic en **Invocar** para aplicar el nuevo valor al objeto.  
  
     La propiedad contiene ahora el nuevo valor.  
  
#### Para probar eventos y especificar el destino de la información de eventos.  
  
1.  En el menú de **Opciones recomendadas** , haga clic en **Registro**.  
  
2.  Especifique el destino de la información de eventos.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Cómo: Depurar un control ActiveX](../Topic/How%20to:%20Debug%20an%20ActiveX%20Control.md)