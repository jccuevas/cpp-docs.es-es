---
title: "Determinar el m&#233;todo de vinculaci&#243;n que se debe utilizar | Microsoft Docs"
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
  - "vinculación explícita [C++]"
  - "vinculación implícita [C++]"
ms.assetid: 6b6d3fec-4711-4a30-af5b-354b965ecaec
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Determinar el m&#233;todo de vinculaci&#243;n que se debe utilizar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Existen dos tipos de vinculación: vinculación implícita y vinculación explícita.  
  
## Vinculación implícita  
 [La vinculación implícita](../build/linking-implicitly.md) se produce cuando el código de una aplicación llama a una función exportada de un archivo DLL.  Cuando se compila o ensambla el código fuente para el archivo ejecutable de llamada, la llamada a la función del archivo DLL genera una referencia de función externa en el código objeto.  Para resolver esta referencia externa, la aplicación debe vincularse a la biblioteca de importación \(archivo .LIB\) proporcionada por el autor del archivo DLL.  
  
 La biblioteca de importación sólo contiene código para cargar el archivo DLL e implementar llamadas a las funciones del archivo DLL.  Cuando se encuentra una función externa en una biblioteca de importación, se notifica al vinculador que el código de la función está en un archivo DLL.  Para resolver referencias externas a archivos DLL, el vinculador simplemente agregará información al archivo ejecutable para indicar al sistema dónde se encuentra el código del archivo DLL cuando se inicie el proceso.  
  
 Cuando el sistema inicia un programa que contiene referencias vinculadas dinámicamente, utiliza esta información en el archivo ejecutable del programa para encontrar los archivos DLL necesarios.  Si no encuentra el archivo DLL, el sistema finalizará el proceso y mostrará un cuadro de diálogo para notificar el error.  En caso contrario, el sistema asigna los módulos de DLL al espacio de direcciones del proceso.  
  
 Si alguno de los archivos DLL tiene una función de punto de entrada \(para el código de inicialización y finalización\), el sistema operativo llamará a la función.  Uno de los parámetros pasados a la función de punto de entrada especifica un código que indica que se está asociando el archivo DLL al proceso.  Si la función de punto de entrada no devuelve el valor TRUE, el sistema finalizará el proceso y notificará un error.  
  
 Por último, el sistema modifica el código ejecutable del proceso para proporcionar direcciones de inicio a las funciones del archivo DLL.  
  
 Como el resto del código de un programa, el código de un archivo DLL se asigna al espacio de direcciones del proceso cuando éste se inicie y sólo se carga en memoria cuando sea necesario.  Como resultado, los atributos de código **PRELOAD** y **LOADONCALL** utilizados por los archivos .DEF para controlar la carga en las versiones anteriores de Windows ya no tienen sentido.  
  
## Vinculación explícita  
 La mayoría de las aplicaciones utilizan la vinculación implícita, puesto que es el método de vinculación más sencillo de utilizar.  Sin embargo, a veces es necesario utilizar la [vinculación explícita](../build/linking-explicitly.md).  Algunas de las razones más frecuentes para utilizar la vinculación explícita son:  
  
-   La aplicación no conoce hasta el momento de ejecución el nombre de un archivo DLL que tiene que cargar.  Por ejemplo, la aplicación puede necesitar obtener el nombre del archivo DLL y las funciones exportadas desde un archivo de configuración.  
  
-   El sistema operativo finaliza un proceso que utiliza la vinculación implícita si no se encuentra el archivo DLL en el inicio del proceso.  Un proceso que utilice vinculación explícita no finaliza en esta situación y puede intentar recuperarse del error.  Por ejemplo, podría notificar el error al usuario y pedirle que especifique otra ruta de acceso al archivo DLL.  
  
-   Un proceso que utilice vinculación implícita también finaliza si cualquiera de los archivos DLL a los que esté vinculado incluye una función `DllMain` que produce errores.  Un proceso que utilice vinculación explícita no finaliza en esta situación.  
  
-   Una aplicación que se vincule implícitamente a muchos archivos DLL puede resultar lenta de inicializar, puesto que Windows cargará todos los archivos DLL cuando se cargue la aplicación.  Para mejorar el rendimiento de inicio, una aplicación puede vincularse implícitamente a esos archivos DLL necesarios inmediatamente después de la carga y esperar a vincularse explícitamente a los demás archivos DLL cuando sean necesarios.  
  
-   La vinculación explícita elimina la necesidad de vincular la aplicación a una biblioteca de importación.  Si los cambios realizados a la DLL hacen que cambien los ordinales de exportación, las aplicaciones que utilicen la vinculación explícita no tendrán que volver a vincular \(si llaman a **GetProcAddress** con un nombre de una función, no con un valor ordinal\), mientras que las aplicaciones que utilicen la vinculación implícita deberán volver a vincularse a la nueva biblioteca de importación.  
  
 Hay que tener en cuenta dos posibles peligros en la vinculación explícita:  
  
-   Si el archivo DLL tiene una función de punto de entrada `DllMain`, el sistema operativo llamará a la función en el contexto del subproceso que llamó a **LoadLibrary**.  No se llamará a la función de punto de entrada si el archivo DLL ya está asociado al proceso a causa de una llamada anterior a **LoadLibrary** sin una llamada correspondiente a la función **FreeLibrary**.  La vinculación explícita puede producir problemas si el archivo DLL utiliza la función `DllMain` para realizar la inicialización de cada subproceso de un proceso, puesto que no se inicializarán los subprocesos existentes al llamar a **LoadLibrary** \(o `AfxLoadLibrary`\).  
  
-   Si un archivo DLL declara datos de extensión estática como **\_\_declspec\(thread\)**, puede producirse un error de protección si el archivo se vincula explícitamente.  Después de cargar el archivo DLL mediante **LoadLibrary**, se producirá un error de protección siempre que el código haga referencia a estos datos. Entre los datos de extensión estática se incluyen elementos estáticos globales y locales. Por tanto, al crear un archivo DLL, deberá evitar el uso de almacenamiento local de subprocesos y no deberá informar a los usuarios del archivo DLL acerca de los posibles errores \(en caso de que intenten la carga dinámica\).  
  
## ¿Qué desea hacer?  
  
-   [Vincular de forma implícita](../build/linking-implicitly.md)  
  
-   [Vincular de forma explícita](../build/linking-explicitly.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [La ruta de acceso de búsqueda que Windows utiliza para buscar una DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
-   [FreeLibrary y AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [\<caps:sentence id\="tgt47" sentenceid\="8081a197f9413cac12a30b57c2612af5" class\="tgtSentence"\>Utilizar almacenamiento local de subprocesos en una biblioteca de vínculos dinámicos \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms686997)  
  
## Vea también  
 [Vincular un ejecutable a un archivo DLL](../build/linking-an-executable-to-a-dll.md)