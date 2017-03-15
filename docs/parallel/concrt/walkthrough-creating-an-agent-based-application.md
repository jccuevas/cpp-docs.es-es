---
title: "Tutorial: Crear una aplicaci&#243;n basada en agente | Microsoft Docs"
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
  - "agentes asincrónicos, crear"
  - "agent (clase), ejemplo"
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Tutorial: Crear una aplicaci&#243;n basada en agente
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se describe cómo crear una aplicación basada en agente básica.  En este tutorial, puede crear un agente que lee datos de un archivo de texto de forma asincrónica.  La aplicación utiliza el algoritmo de suma de comprobación Adler\-32 para calcular la suma de comprobación del contenido de ese archivo.  
  
## Requisitos previos  
 Para completar este tutorial, debe comprender los siguientes temas:  
  
-   [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)  
  
-   [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)  
  
-   [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> Secciones  
 En este tutorial se muestra cómo realizar las tareas siguientes:  
  
-   [Crear la aplicación de consola](#createApplication)  
  
-   [Crear la clase file\_reader](#createAgentClass)  
  
-   [Usar la clase file\_reader en la aplicación](#useAgentClass)  
  
##  <a name="createApplication"></a> Crear la aplicación de consola  
 En esta sección se muestra cómo crear una aplicación de consola de Visual C\+\+ que hace referencia a los archivos de encabezado que el programa usará.  
  
#### Para crear una aplicación Visual C\+\+ utilizando el Asistente para aplicación de consola Win32  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en el panel **Tipos de proyecto**, seleccione el nodo **Visual C\+\+** y, a continuación, seleccione **Aplicación de consola Win32** en el panel **Plantillas**.  Escriba un nombre para el proyecto, por ejemplo, `BasicAgent` y, a continuación, haga clic en **Aceptar** para mostrar el **Asistente para aplicación de consola Win32**.  
  
3.  En el cuadro de diálogo **Asistente para aplicación de consola Win32**, haga clic en **Finalizar**.  
  
4.  En stdafx.h, agregue el código siguiente.  
  
     [!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_1.h)]  
  
     El archivo de encabezado agents.h contiene la funcionalidad de la clase [concurrency::agent](../../parallel/concrt/reference/agent-class.md).  
  
5.  Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela.  Para compilar la aplicación, en el menú **Generar**, haga clic en **Generar solución**.  Si la aplicación se compila correctamente, haga clic en **Iniciar depuración** en el menú **Depurar** para ejecutarla.  
  
 \[[Arriba](#top)\]  
  
##  <a name="createAgentClass"></a> Crear la clase file\_reader  
 En esta sección se muestra cómo crear la clase `file_reader`.  El runtime programa cada agente para realizar el trabajo en su propio contexto.  Por tanto, puede crear un agente que realice el trabajo de forma sincrónica pero que interactúe con otros componentes de forma asincrónica.  La clase `file_reader` lee los datos de un archivo de entrada determinado y los envía desde este archivo a un componente de destino determinado.  
  
#### Para crear la clase file\_reader  
  
1.  Agregue un nuevo archivo de encabezado de C\+\+ al proyecto.  Para ello, en el **Explorador de soluciones**, haga clic con el botón secundario en el nodo **Archivos de encabezado**, haga clic en **Agregar** y, a continuación, haga clic en **Nuevo elemento**.  En el panel **Plantillas**, seleccione **Archivo de encabezado \(.h\)**.  En el cuadro de diálogo **Agregar nuevo elemento**, escriba `file_reader.h` en el cuadro **Nombre** y haga clic en **Agregar**.  
  
2.  En file\_reader.h, agregue el siguiente código.  
  
     [!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_2.h)]  
  
3.  En file\_reader.h, cree una clase de nombre `file_reader` que derive de `agent`.  
  
     [!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_3.h)]  
  
4.  Agregue los siguientes miembros de datos a la sección `private` de la clase.  
  
     [!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_4.h)]  
  
     El miembro `_file_name` es el nombre de archivo del que lee el agente.  El miembro `_target` es un objeto [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) en el que el agente escribe el contenido del archivo.  El miembro `_error` contiene cualquier error que se produce durante la vida del agente.  
  
5.  Agregue el código siguiente para los constructores de `file_reader` en la sección `public` de la clase `file_reader`.  
  
     [!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_5.h)]  
  
     Cada sobrecarga de constructor establece los miembros de datos de `file_reader`.  La segunda y tercera sobrecarga de constructor permiten que la aplicación use un programador concreto con el agente.  La primera sobrecarga utiliza el programador predeterminado con el agente.  
  
6.  Agregue el método `get_error` a la sección pública de la clase `file_reader`.  
  
     [!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_6.h)]  
  
     El método `get_error` recupera cualquier error que se produce durante la vida del agente.  
  
7.  Implemente el método [concurrency::agent::run](../Topic/agent::run%20Method.md) en la sección `protected` de la clase.  
  
     [!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_7.h)]  
  
     El método `run` abre el archivo y lee sus datos.  El método `run` utiliza el control de excepciones para capturar los errores que se produzcan durante el procesamiento del archivo.  
  
     Cada vez que este método lee datos del archivo, llama a la función [concurrency::asend](../Topic/asend%20Function.md) para enviar esos datos al búfer de destino.  Envía la cadena vacía a su búfer de destino para indicar el fin del procesamiento.  
  
 En el ejemplo siguiente se muestra el contenido completo de file\_reader.h.  
  
 [!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_8.h)]  
  
 \[[Arriba](#top)\]  
  
##  <a name="useAgentClass"></a> Usar la clase file\_reader en la aplicación  
 En esta sección se muestra cómo utilizar la clase `file_reader` para leer el contenido de un archivo de texto.  También se muestra cómo crear un objeto [concurrency::call](../../parallel/concrt/reference/call-class.md) que recibe los datos de este archivo y calcula su suma de comprobación Adler\-32.  
  
#### Para utilizar la clase file\_reader en la aplicación  
  
1.  En BasicAgent.cpp, agregue la siguiente instrucción `#include`.  
  
     [!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_9.cpp)]  
  
2.  En BasicAgent.cpp, agregue las siguientes directivas `using`.  
  
     [!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_10.cpp)]  
  
3.  En la función `_tmain`, cree un objeto [concurrency::event](../../parallel/concrt/reference/event-class.md) que indique el fin del procesamiento.  
  
     [!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_11.cpp)]  
  
4.  Cree un objeto `call` que actualice la suma de comprobación cuando reciba datos.  
  
     [!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_12.cpp)]  
  
     Este objeto `call` también establece el objeto `event` cuando recibe la cadena vacía para señalar el fin del procesamiento.  
  
5.  Cree un objeto `file_reader` que lea del archivo test.txt y escriba el contenido de este archivo en el objeto `call`.  
  
     [!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_13.cpp)]  
  
6.  Inicie el agente y espere a que finalice.  
  
     [!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_14.cpp)]  
  
7.  Espere a que el objeto `call` reciba todos los datos y finalice.  
  
     [!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_15.cpp)]  
  
8.  Compruebe los errores del lector del archivo.  Si no se ha producido ningún error, calcule la suma Adler\-32 final e imprímala en la consola.  
  
     [!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_16.cpp)]  
  
 En el ejemplo siguiente se muestra el archivo BasicAgent.cpp completo.  
  
 [!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_17.cpp)]  
  
 \[[Arriba](#top)\]  
  
## Entrada de ejemplo  
 Este es el contenido de ejemplo del archivo de entrada text.txt:  
  
  **The quick brown fox**  
**jumps**  
**over the lazy dog**   
## Resultados del ejemplo  
 Cuando se utiliza con la entrada de ejemplo, este programa produce el siguiente resultado:  
  
  **Adler\-32 sum is fefb0d75**   
## Programación sólida  
 Para evitar el acceso simultáneo a los miembros de datos, se recomienda agregar métodos que realicen el trabajo en las secciones `protected` o `private` de la clase.  Agregue únicamente los métodos que envían o reciben mensajes del agente en la sección `public` de la clase.  
  
 Llame siempre al método [concurrency::agent::done](../Topic/agent::done%20Method.md) para mover el agente al estado completado.  Por lo general se llama a este método antes de volver del método `run`.  
  
## Pasos siguientes  
 Para obtener otro ejemplo de una aplicación basada en agente, vea [Tutorial: Usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).  
  
## Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)   
 [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)   
 [Tutorial: Usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)