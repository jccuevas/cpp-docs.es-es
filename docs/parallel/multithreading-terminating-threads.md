---
title: "Subprocesamiento m&#250;ltiple: Finalizar subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATE_SUSPENDED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxEndThread (método)"
  - "subprocesamiento múltiple [C++], terminar subprocesos"
  - "terminación prematura de subprocesos"
  - "iniciar subprocesos"
  - "detener subprocesos"
  - "terminar subprocesos"
  - "subprocesamiento [C++], detener subprocesos"
  - "subprocesamiento [MFC], terminar subprocesos"
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple: Finalizar subprocesos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un subproceso puede terminar en dos situaciones normales: la función controladora finaliza o el subproceso no llega a completarse.  Si un procesador de texto utiliza un subproceso para impresión de fondo, la función controladora terminaría normalmente si la impresión se completa sin problemas.  Si el usuario desea cancelar la impresión, el subproceso de impresión de fondo debe terminarse prematuramente.  Este tema explica cómo implementar cada situación y cómo obtener el código de salida de un subproceso después de que termine.  
  
-   [Terminación normal de un subproceso](#_core_normal_thread_termination)  
  
-   [Terminación prematura de un subproceso](#_core_premature_thread_termination)  
  
-   [Recuperar el código de salida de un subproceso](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> Terminación normal de un subproceso  
 Para un subproceso de trabajo, la terminación normal es simple: salir de la función controladora y devolver un valor que indique el motivo de la terminación.  Se puede utilizar la función [AfxEndThread](../Topic/AfxEndThread.md) o una instrucción `return`.  Normalmente, 0 significa terminación sin error, pero se trata de una convención que se puede cambiar.  
  
 Para un subproceso de interfaz de usuario, el proceso también es simple: desde el subproceso, se debe llamar a la función [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) de [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  El único parámetro que utiliza **PostQuitMessage** es el código de salida del subproceso.  Al igual que para subprocesos de trabajo, 0 suele significar terminación sin errores.  
  
##  <a name="_core_premature_thread_termination"></a> Terminación prematura de un subproceso  
 Terminar un subproceso de forma prematura es también muy simple: realice una llamada a [AfxEndThread](../Topic/AfxEndThread.md) desde dentro del subproceso.  Pase el código de salida deseado como único parámetro.  Esto hace que la ejecución del subproceso se detenga, libere la pila del subproceso, desconecte todas las DLL conectadas al subproceso y elimine el objeto de subproceso de la memoria.  
  
 La llamada a `AfxEndThread` debe hacerse desde dentro del subproceso que se va a terminar.  Si se desea terminar el subproceso desde otro subproceso, se debe establecer un método de comunicación entre ambos subprocesos.  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> Recuperar el código de salida de un subproceso  
 Para obtener el código de salida de un subproceso de trabajo o de interfaz de usuario, se debe llamar a la función [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  Para obtener más información sobre esta función, vea [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  Esta función recibe el identificador del subproceso \(almacenado en el miembro de datos `m_hThread` de los objetos `CWinThread`\) y la dirección de una `DWORD`.  
  
 Si el subproceso está aún activo, **GetExitCodeThread** coloca **STILL\_ACTIVE** en la dirección `DWORD` suministrada; de lo contrario, es el código de salida el que se coloca en esta dirección.  
  
 Recuperar el código de salida de los objetos [CWinThread](../mfc/reference/cwinthread-class.md) requiere un paso adicional.  De forma predeterminada, cuando un subproceso `CWinThread` termina, el objeto de subproceso se elimina.  Esto significa que no es posible obtener acceso al miembro de datos `m_hThread`, ya que el objeto `CWinThread` ya no existe.  Para evitar esta situación, realice una de las acciones siguientes:  
  
-   Asigne al miembro de datos `m_bAutoDelete` el valor **FALSE**.  Esto permite que el objeto `CWinThread` sobreviva después de que el subproceso haya terminado.  Entonces, es posible obtener acceso al miembro de datos `m_hThread`.  No obstante, si utiliza esta técnica, debe destruir explícitamente el objeto `CWinThread`, ya que el marco de trabajo no lo eliminará automáticamente.  Éste es el método preferido.  
  
-   Almacene el identificador del subproceso de forma independiente.  Después de haber creado el subproceso, copie su miembro de datos `m_hThread` \(mediante **::DuplicateHandle**\) a otra variable y realice el acceso a él a través de esa variable.  De esta forma, el objeto se elimina automáticamente después de su terminación y aún es posible conocer por qué terminó el subproceso.  Asegúrese de que el subproceso no termina antes de poder duplicar el identificador.  El método más seguro para hacerlo consiste en pasar **CREATE\_SUSPENDED** a [AfxBeginThread](../Topic/AfxBeginThread.md), almacenar el identificador y, a continuación, reanudar el subproceso mediante una llamada a [ResumeThread](../Topic/CWinThread::ResumeThread.md).  
  
 Cualquiera de los métodos permite determinar por qué termina un objeto `CWinThread`.  
  
## Vea también  
 [Subprocesamiento múltiple con C\+\+ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)   
 [\_endthread, \_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
 [\_beginthread, \_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)