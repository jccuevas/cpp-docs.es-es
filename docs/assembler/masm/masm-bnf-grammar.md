---
title: Gramática de BNF de Microsoft macro Assembler
description: Descripción de BNF de MASM para x64.
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), BNF reference
ms.openlocfilehash: 29eae0b110f99f1f417e153f18aa2ac3aff5c69b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322827"
---
# <a name="microsoft-macro-assembler-bnf-grammar"></a>Gramática de BNF de Microsoft macro Assembler

Esta página contiene una descripción BNF de la gramática de MASM. Se proporciona como complemento a los temas de referencia y no se garantiza que esté completo. Consulte los temas de referencia para obtener información completa sobre las palabras clave, los parámetros, las operaciones, etc.

Para ilustrar el uso de BNF, en el diagrama siguiente se muestra la definición de la Directiva TYPEDEF, comenzando por el *typedefDir*nonterminal.

![Ejemplo de BNF de MASM](media/bnf.png)

Las entradas de cada llave horizontal son terminales (como **NEAR16**, **NEAR32**, **FAR16**y **FAR32**) o no terminales (como *calificador*, *qualifiedType*, *distancia*y *protoSpec*) que se pueden definir aún más. Cada no terminal en cursiva en la definición de *typedefDir* también es una entrada en el BNF. Tres puntos verticales indican una definición de bifurcación para un no terminal que, por motivos de simplicidad, no se muestra en esta ilustración.

La gramática BNF permite definiciones recursivas. Por ejemplo, la gramática usa qualifiedType como una posible definición para qualifiedType, que también es un componente de la definición de calificador. El símbolo "|" especifica una opción entre expresiones alternativas, por ejemplo, *endOfLine* | *Comentario*. Las llaves dobles especifican un parámetro opcional, por ejemplo, ⟦ *macroParmList* ⟧. En realidad, los corchetes no aparecen en el código fuente.

## <a name="masm-nonterminals"></a>No terminales de MASM

*;;* \
&nbsp;&nbsp;&nbsp;&nbsp;*endOfLine* | *Comentario*

*= Dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* = *immExpr* ;;

\ *addOp*
&nbsp;&nbsp;&nbsp;&nbsp;+ | -

\ *aExpr*
&nbsp;&nbsp;&nbsp;&nbsp;*término* | *aExpr* && 

\ *altId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *arbitraryText*
&nbsp;&nbsp;&nbsp;&nbsp;*charList*

\ *asmInstruction*
&nbsp;&nbsp;&nbsp;&nbsp;*mnemotécnico* ⟦ *exprList* ⟧

\ *assumeDir*
&nbsp;&nbsp;&nbsp;&nbsp;**asuma** *assumeList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| no **suponen nada** ;;

\ *assumeList*
&nbsp;&nbsp;&nbsp;&nbsp;*assumeRegister* | *assumeList* , *assumeRegister*\

\ *assumeReg*
&nbsp;&nbsp;&nbsp;&nbsp;*registro* : *assumeVal*

\ *assumeRegister*
&nbsp;&nbsp;&nbsp;&nbsp;*assumeSegReg* | *assumeReg*

\ *assumeSegReg*
&nbsp;&nbsp;&nbsp;&nbsp;*segmentRegister* : *assumeSegVal*

\ *assumeSegVal*
&nbsp;&nbsp;&nbsp;&nbsp;*frameExpr* | **Nothing** | **error**

\ *assumeVal*
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **Nothing** | **error**

\ *bcdConst*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Sign* ⟧ *decNumber*

\ *binaryOp*
&nbsp;&nbsp;&nbsp;&nbsp;= = |! = | > = | < = | > | < | &

\ *bitDef*
&nbsp;&nbsp;&nbsp;&nbsp;*bitFieldId* : *BitFieldSize* ⟦ = *constExpr* ⟧

\ *bitDefList*
&nbsp;&nbsp;&nbsp;&nbsp;*bitDef* | *bitDefList* , ⟦;; ⟧ *bitDef*

\ *bitFieldId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *bitFieldSize*
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

\ *blockStatements*
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Continúe** **. Si** *cExpr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. INTERRUMPA** ⟦ **. Si** *cExpr* ⟧

*bool*\
&nbsp;&nbsp;&nbsp;&nbsp;**TRUE** | **false**

\ *byteRegister*
&nbsp;&nbsp;&nbsp;&nbsp;AL | AH | CL | CH | DL | DH | BL | BH | R8B | R9B | R10B | R11B | R12B | R13B | R14B | R15B

\ *cExpr*
&nbsp;&nbsp;&nbsp;&nbsp;*aExpr* | *cExpr* || *aExpr*

\ de *caracteres*
&nbsp;&nbsp;&nbsp;&nbsp;cualquier carácter que tenga el ordinal en el intervalo comprendido entre 0 y 255, excepto el avance de la letra (10).

\ *charList*
&nbsp;&nbsp;&nbsp;&nbsp;*carácter* de *listacaracteres* | 

\ *className*
&nbsp;&nbsp;&nbsp;&nbsp;*cadena*

\ *commDecl*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *nearfar* ⟧ ⟦ *langType* ⟧ *ID* : *commType*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦: *constExpr* ⟧

\ *commDir*
&nbsp;&nbsp;&nbsp;&nbsp;**COMM**\
&nbsp;&nbsp;&nbsp;&nbsp;*commList* ;;

*comentario*\
&nbsp;&nbsp;&nbsp;&nbsp;; *texto* ;;

\ *commentDir*
&nbsp;&nbsp;&nbsp;&nbsp; *delimitador* de comentario\
&nbsp;&nbsp;&nbsp;&nbsp;*texto*\
&nbsp;&nbsp;&nbsp;&nbsp;*texto* del *delimitador* de *texto* ;;

\ *commList*
&nbsp;&nbsp;&nbsp;&nbsp;*commDecl* | *commList* , *commDecl*

\ *commType*
&nbsp;&nbsp;&nbsp;&nbsp;*tipo* | *constExpr*

\ *constante*
&nbsp;&nbsp;&nbsp;&nbsp;*dígitos* ⟦ *radixOverride* ⟧

\ *constExpr*
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

\ *contextDir*
&nbsp;&nbsp;&nbsp;&nbsp;**PUSHCONTEXT** *contextItemList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;**POPCONTEXT** *contextItemList* ;;

\ *contextItem*
&nbsp;&nbsp;&nbsp;&nbsp;**presupone** | **base** | **enumera** | **CPU** | **todo**

\ *contextItemList*
&nbsp;&nbsp;&nbsp;&nbsp;*contextItem* | *contextItemList* , *contextItem*

\ *controlBlock*
&nbsp;&nbsp;&nbsp;&nbsp;*whileBlock* | *repeatBlock*

\ *controlDir*
&nbsp;&nbsp;&nbsp;&nbsp;*controlIf* | *controlBlock*

\ *controlElseif*
&nbsp;&nbsp;&nbsp;&nbsp; **. ELSEIF** &nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧

\ *controlIf*
&nbsp;&nbsp;&nbsp;&nbsp; **. Si** &nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **. ELSE** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;[*directiveList*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp; **. ENDIF** ;;

\ del *coprocesador*
&nbsp;&nbsp;&nbsp;&nbsp;. 8087 |. 287 |. 387 |. NO87

\ *crefDir*
&nbsp;&nbsp;&nbsp;&nbsp;*crefOption* ;;

\ *crefOption*
&nbsp;&nbsp;&nbsp;&nbsp; **. CREF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. XCREF** ⟦ *idList* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOCREF** ⟦ *idList* ⟧

\ *cxzExpr*
&nbsp;&nbsp;&nbsp;&nbsp;*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;|! *expr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* = = expr \
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* ! = expr

\ *dataDecl*
&nbsp;&nbsp;&nbsp;&nbsp;DB | DW | DD | DF | DQ | DT | *datatype* | *typeId*

*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧ *;;*

\ de *DataItem*
&nbsp;&nbsp;&nbsp;&nbsp;*dataDecl* *scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag* *recordInstList*

\ *DataType*
&nbsp;&nbsp;&nbsp;&nbsp;BYTE | SBYTE | PALABRA | ESPADA | DWORD | SDWORD | FWORD | QWORD | SQWORD | - OWORD | REAL4 | REAL8 | REAL10 | MMWORD | XMMWORD | YMMWORD

\ *decdigit*
&nbsp;&nbsp;&nbsp;&nbsp;0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

\ *decNumber*
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *decNumber* *decdigit*

*delimitador*\
&nbsp;&nbsp;&nbsp;&nbsp;cualquier carácter excepto *whiteSpaceCharacter*

*dígitos*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dígitos* *decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dígitos* hexdigit

*directiva*\
&nbsp;&nbsp;&nbsp;&nbsp;*generalDir* | *segmentDef*

\ *directiveList*
&nbsp;&nbsp;&nbsp;&nbsp;*directiva* | *directiveList*

\ de *distancia*
&nbsp;&nbsp;&nbsp;&nbsp;*nearfar* | **NEAR16** | **NEAR32** | **FAR16** | **FAR32**

\ *0E01*
&nbsp;&nbsp;&nbsp;&nbsp;0E01 *orOp* *E02* | *E02*

\ *E02*
&nbsp;&nbsp;&nbsp;&nbsp;E02 **y** *E03* | *E03*

\ *E03*
&nbsp;&nbsp;&nbsp;**no** &nbsp;*E04* | *E04*

\ *E04*
&nbsp;&nbsp;&nbsp;&nbsp;*E04* *relOp* *E05* | *E05*

\ *E05*
&nbsp;&nbsp;&nbsp;&nbsp;*E05* *addOp* *E06* | *E06*

\ *E06*
&nbsp;&nbsp;&nbsp;&nbsp;*E06* *mulOp* *e07* | *E06* *shiftOp* *E07* | *E07*

\ *E07*
&nbsp;&nbsp;&nbsp;&nbsp;*E07* *addOp* *E08* | *E08*

\ *E08*
&nbsp;&nbsp;&nbsp;&nbsp;**High** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Low** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **HIGHWORD** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LOWWORD** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09*

\ *E09*
&nbsp;&nbsp;&nbsp;&nbsp;**PosiciónInicial** *E10*\
&nbsp;&nbsp;&nbsp; **&nbsp;| en** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LROFFSET** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **tipo** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **este** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* **ptr** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* : *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E10*

\ *E10*
&nbsp;&nbsp;&nbsp;&nbsp;*E10* . \ *E11*
&nbsp;&nbsp;&nbsp;&nbsp;| *E10* ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *E11*

\ *E11*
&nbsp;&nbsp;&nbsp;&nbsp;( *expr* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  *ID.* de ancho\
&nbsp;&nbsp;&nbsp;&nbsp;*identificador* de **máscara** | 
&nbsp;&nbsp;&nbsp;&nbsp;| **tamaño** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **sizeof** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*identificador* de **longitud** | \
&nbsp;&nbsp;&nbsp;&nbsp;|  *identificador* de longitud\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;| *cadena*\
&nbsp;&nbsp;&nbsp;&nbsp;| *constante*\
&nbsp;&nbsp;&nbsp;&nbsp;| *tipo*\
&nbsp;&nbsp;&nbsp;&nbsp;| *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **$**\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;| *registro*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST**\
&nbsp;&nbsp;&nbsp;&nbsp;| **St** ( *expr* )

\ *echoDir*
&nbsp;&nbsp;&nbsp;&nbsp;**eco**\
&nbsp;&nbsp;&nbsp;&nbsp;*arbitraryText* ;; \
%**out** *arbitraryText* ;; \

\ *elseifBlock*
&nbsp;&nbsp;&nbsp;&nbsp;*elseifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \

\ *elseifStatement*
&nbsp;&nbsp;&nbsp;&nbsp;**ELSEIF** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseifdef (** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseifndef (** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIF** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIFI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDN** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDNI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF2**

\ *endDir*
&nbsp;&nbsp;&nbsp;&nbsp;**End** ⟦ *immExpr* ⟧;;

\ *endpDir*
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **ENDP** ;;

\ *endsDir*
&nbsp;&nbsp;&nbsp;*ID.* de &nbsp;**finaliza** ;

\ *equDir*
&nbsp;&nbsp;&nbsp;&nbsp;*textMacroId* **equ** *equType* ;;

\ *equType*
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr* | *textLiteral*

\ *errorDir*
&nbsp;&nbsp;&nbsp;&nbsp;*errorOpt* ;;

\ *errorOpt*
&nbsp;&nbsp;&nbsp;&nbsp; **. ERR** ⟦ *textItem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRE** *constExpr* ⟦ *optText* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNZ** *constExpr* ⟦ *optText* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRB** *textItem* ⟦ *optText* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNB** *textItem* ⟦ *optText* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDEF** *ID* ⟦ *optText* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNDEF** *ID* ⟦ *optText* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIF** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIFI** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDN** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDNI** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR1** ⟦ *textItem* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR2** ⟦ *textItem* ⟧

\ *exitDir*
&nbsp;&nbsp;&nbsp;&nbsp; **. EXIT** &nbsp;&nbsp;&nbsp;&nbsp;⟦ *expr* ⟧;;

\ *exitmDir*
&nbsp;&nbsp;&nbsp;&nbsp;: EXITM | EXITM *textItem*

\ *exponente*
&nbsp;&nbsp;&nbsp;&nbsp;E ⟦ *Sign* ⟧ *decNumber*

*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;**Short** *E05*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Escriba** 0E01 \
&nbsp;&nbsp;&nbsp;&nbsp;| **OPATTR** *0E01*\
&nbsp;&nbsp;&nbsp;&nbsp;| *0E01*

\ *exprList*
&nbsp;&nbsp;&nbsp;&nbsp;*expr* | *exprList* , *expr*

\ *externDef*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧ *ID* ⟦ ( *altId* ) ⟧: *externType*

\ *externDir*
&nbsp;&nbsp;&nbsp;&nbsp;*externKey* *externList* ;;

\ *externKey*
&nbsp;&nbsp;&nbsp;&nbsp;**EXTRN** | **extern** | **EXTERNDEF**

\ *externList*
&nbsp;&nbsp;&nbsp;&nbsp;*externDef* | *externList* , ⟦;; ⟧ *externDef*

\ *externType*
&nbsp;&nbsp;&nbsp;&nbsp;**ABS** | *qualifiedType*

\ *fieldAlign*
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

\ *fieldInit*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *initValue* ⟧ | *structInstance*

\ *fieldInitList*
&nbsp;&nbsp;&nbsp;&nbsp;*fieldInit* | *fieldInitList* , ⟦;; ⟧ *fieldInit*

\ *fileChar*
&nbsp;&nbsp;&nbsp;*delimitador* de &nbsp;

\ *fileCharList*
&nbsp;&nbsp;&nbsp;&nbsp;*fileChar* | *fileCharList* *fileChar*

*fileSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileCharList* | *textLiteral*

\ *flagName*
&nbsp;&nbsp;&nbsp;&nbsp;**cero?****¿ | transportar?****¿ | Overflow?****¿ | signo?** | **paridad?**

\ *floatNumber*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Sign* ⟧ *decNumber* . ⟦ *decNumber* ⟧ ⟦ *exponente* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *dígitos* R | *dígitos* r

\ *forcDir*
&nbsp;&nbsp;&nbsp;&nbsp;**FORC** | **IRPC**

\ *forDir*
&nbsp;&nbsp;&nbsp;&nbsp;**para** | **IRP**

\ *forParm*
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦: *forParmType* ⟧

\ *forParmType*
&nbsp;&nbsp;&nbsp;&nbsp;**req** | = *textLiteral*

\ *fpuRegister*
&nbsp;&nbsp;&nbsp;&nbsp;**St** *expr*

\ *frameExpr*
&nbsp;&nbsp;&nbsp;&nbsp; *ID.* de seg\
&nbsp;&nbsp;&nbsp;&nbsp;| **DGROUP** : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister* : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* | 

\ *generalDir*
&nbsp;&nbsp;&nbsp;&nbsp;*modelDir* | *segOrderDir* | *nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *includeLibDir* | *commentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *groupDir* | *assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structDir* | *recordDir* | *typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *externDir* | *publicDir* | *commDir* | *protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *equDir* | = Dir |\ *textDir*
&nbsp;&nbsp;&nbsp;&nbsp;| *contextDir* | *optionDir* | *processorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *titleDir* | *pageDir* | *listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *crefDir* | *echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ifDir* | *errorDir* | *includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroDir* | *macroCall* | *macroRepeat* | *purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroWhile* | *macroFor* | *macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;| *aliasDir*

\ *gpRegister*
&nbsp;&nbsp;&nbsp;&nbsp;AX | EAX | CX | ECX | DX | EDX | BX | EBX | DI | EDI | SI | ESI | BP | EBP | SP | ESP | RSP | R8W | R8D | R9W | R9D | R12D | R13W | R13D | R14W | R14D

\ *groupDir*
&nbsp;&nbsp;&nbsp;&nbsp;*GROUPID* **Group** *segIdList*

\ *GROUPID*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *hexdigit*
&nbsp;&nbsp;&nbsp;&nbsp;un | b | c | d | e | f | Un | B | C | D | E | Formato

*identificador*\
&nbsp;&nbsp;&nbsp;&nbsp;el primer carácter del identificador puede ser un carácter alfabético en mayúsculas o minúsculas (`[A–Za-z]`) o cualquiera de estos cuatro caracteres: `@ _ $ ?` el resto de caracteres puede ser cualquiera de esos mismos caracteres o un dígito decimal (`[0–9]`). La longitud máxima es de 247 caracteres.

\ *idList*
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *idList* , *ID*

\ *ifDir*
&nbsp;&nbsp;&nbsp;&nbsp;*ifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \
&nbsp;&nbsp;&nbsp; **&nbsp;⟦;;** \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* ⟧;; \

\ *ifStatement*
&nbsp;&nbsp;&nbsp;&nbsp;**si** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifdef** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifndef** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIF** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIFI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDN** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDNI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF2**

\ *immExpr*
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

\ *includeDir*
&nbsp;&nbsp;&nbsp;&nbsp;**incluir** *fileSpec* ;;

\ *includeLibDir*
&nbsp;&nbsp;&nbsp;&nbsp;**includelib (** *fileSpec* ;;

\ *initValue*
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *cadena*\
&nbsp;&nbsp;&nbsp;&nbsp;|? \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *scalarInstList* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;| *bcdConst*

\ *inSegDir*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *labelDef* ⟧ *inSegmentDir*

\ *inSegDirList*
&nbsp;&nbsp;&nbsp;&nbsp;*inSegDir* | *inSegDirList* *inSegDir*

\ *inSegmentDir*
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *procDir* ⟦ *localDirList* *⟧ ⟦ inSegDirList* ⟧ *endpDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*

\ *instrPrefix*
&nbsp;&nbsp;&nbsp;&nbsp;**REP** | **REPE** | **REPZ** | **REPNE** | **REPNZ** | **Lock**

\ de *instrucciones*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *instrPrefix* ⟧ *asmInstruction*

\ *invokeArg*
&nbsp;&nbsp;&nbsp;&nbsp;*Register* :: *register* | *expr* | **addr** *expr*

\ *invokeDir*
&nbsp;&nbsp;&nbsp;&nbsp;**INVOKE** *expr* ⟦, ⟦;; ⟧ *invokeList* ⟧;;

\ *invokeList*
&nbsp;&nbsp;&nbsp;&nbsp;*invokeArg* | *invokeList* , ⟦;; ⟧ *invokeArg*

*palabra clave*\
&nbsp;&nbsp;&nbsp;&nbsp;cualquier palabra reservada.

\ *keywordList*
&nbsp;&nbsp;&nbsp;&nbsp;*palabra clave* | *palabra clave* *keywordList*

\ *labelDef*
&nbsp;&nbsp;&nbsp;*id* &nbsp;: | *ID.* :: | @@:

\ *labelDir*
&nbsp;&nbsp;&nbsp;&nbsp; **etiqueta** ID *qualifiedType* ;;

\ *langType*
&nbsp;&nbsp;&nbsp;&nbsp;**C** | **Pascal** | **FORTRAN** | **Basic** | **syscall** | **Stdcall**

\ *listDir*
&nbsp;&nbsp;&nbsp;&nbsp;*listOption* ;;

\ *listOption*
&nbsp;&nbsp;&nbsp;&nbsp; **.** \ de lista
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Nolist**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ XLIST**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ LISTALL**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ LISTIF**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ LFCOND**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ NOLISTIF**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ SFCOND**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ TFCOND**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.**  | LISTMACROALL **.\ LALL**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.**  | NOLISTMACRO **.\ STODAS**
&nbsp;&nbsp;&nbsp;&nbsp;|  **.**  | LISTMACRO **.\ XALL**

\ *localDef*
&nbsp;&nbsp;&nbsp;&nbsp; *idList* local;;

\ *localDir*
&nbsp;&nbsp;&nbsp;&nbsp; *listadeparámetros* local;;

\ *localDirList*
&nbsp;&nbsp;&nbsp;&nbsp;*localDir* | *localDirList* *localDir*

\ *localList*
&nbsp;&nbsp;&nbsp;&nbsp;*localDef* | *localList* *localDef*

\ *macroArg*
 % *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*macroFuncId* ( *macroArgList* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *cadena*\
&nbsp;&nbsp;&nbsp;&nbsp;| *arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;| < *arbitraryText* >

\ *macroArgList*
&nbsp;&nbsp;&nbsp;&nbsp;*macroArg* | *macroArgList* , *macroArg*

\ *macroBody*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *localList* ⟧ *macroStmtList*

\ *macroCall*
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *macroArgList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*identificador* de | ( *macroArgList* )

\ *macroDir*
&nbsp;&nbsp;&nbsp;&nbsp; **macro** ID ⟦ *macroParmList* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

\ *macroFor*
&nbsp;&nbsp;&nbsp;&nbsp;*forDir* *ForParm* , < *macroArgList* >;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

\ *macroForc*
&nbsp;&nbsp;&nbsp;&nbsp;*forcDir* *ID* , *textLiteral* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

\ *macroFuncId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *macroId*
&nbsp;&nbsp;&nbsp;&nbsp;*macroProcId* | *macroFuncId*

\ *macroIdList*
&nbsp;&nbsp;&nbsp;&nbsp;*macroId* | *macroIdList* , *macroId*

\ *macroLabel*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *macroParm*
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦: *parmType* ⟧

\ *macroParmList*
&nbsp;&nbsp;&nbsp;&nbsp;*macroParm* | *macroParmList* , ⟦;; ⟧ *macroParm*

\ *macroProcId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *macroRepeat*
&nbsp;&nbsp;&nbsp;&nbsp;*repeatDir* *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

\ *macroStmt*
&nbsp;&nbsp;&nbsp;&nbsp;*directiva* \
&nbsp;&nbsp;&nbsp;&nbsp;| *exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| : *macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;| **GOTO**\
&nbsp;&nbsp;&nbsp;&nbsp;*macroLabel*

\ *macroStmtList*
&nbsp;&nbsp;&nbsp;&nbsp;*macroStmt* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *macroStmtList* *macroStmt* ;; \

\ *macroWhile*
&nbsp;&nbsp;&nbsp;&nbsp;**durante** *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

\ *mapType*
&nbsp;&nbsp;&nbsp;&nbsp;**todos los** | **ninguno** | **NOTPUBLIC**

\ *memOption*
&nbsp;&nbsp;&nbsp;&nbsp;**diminuto** | **pequeña** | **mediana** | **compacto** | **grande** |  grande | **plano**

\ *mnemotécnico*
&nbsp;&nbsp;&nbsp;&nbsp;nombre de la instrucción.

\ *modelDir*
&nbsp;&nbsp;&nbsp;&nbsp; **.** \ del modelo
&nbsp;&nbsp;&nbsp;&nbsp;*memOption* ⟦, *modelOptlist* ⟧;;

\ *modelOpt*
&nbsp;&nbsp;&nbsp;&nbsp;*langType* | *stackOption*

\ *modelOptlist*
&nbsp;&nbsp;&nbsp;&nbsp;*modelOpt* | *modelOptlist* , *modelOpt*

\ de *módulos*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *directiveList* ⟧ *endDir*

\ *mulOp*
&nbsp;&nbsp;&nbsp;&nbsp;\* | / | **Mod**

\ *nameDir*
&nbsp;&nbsp;&nbsp;&nbsp;**nombre**\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ;; \

\ *nearfar*
&nbsp;&nbsp;&nbsp;&nbsp;**NEAR** | **Far**

\ *nestedStruct*
&nbsp;&nbsp;&nbsp;&nbsp;*structHdr* ⟦ *ID* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**finaliza** ;; \

\ *offsetDir*
&nbsp;&nbsp;&nbsp;&nbsp;*offsetDirType* ;;

\ *offsetDirType*
&nbsp;&nbsp; **&nbsp;&nbsp; | ** **org** *immExpr* | **align** ⟦ *constExpr* ⟧

\ *offsetType*
&nbsp;&nbsp;&nbsp;&nbsp;**grupo** | **segmento** | **plano**

\ *oldRecordFieldList*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* | *oldRecordFieldList* , ⟦ *constExpr* ⟧

\ *optionDir*
&nbsp;&nbsp;&nbsp;&nbsp;**opción** *optionList* ;;

\ *optionItem*
&nbsp;&nbsp;&nbsp;&nbsp;**CASEMAP** : *mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DOTNAME** | **NODOTNAME**\
&nbsp;&nbsp;&nbsp;&nbsp;| **emulador** | **noemulator**\
&nbsp;&nbsp;&nbsp;&nbsp;| **epílogo** : *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **EXPR16** | **EXPR32**\
&nbsp;&nbsp;&nbsp;&nbsp;**lenguaje** de | : *langType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LJMP**
| **NOLJMP**\
&nbsp;&nbsp;&nbsp;&nbsp;| **M510** | **NOM510**\
&nbsp;&nbsp;&nbsp;&nbsp;| **nokeyword** : < *keywordList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOSIGNEXTEND**\
&nbsp;&nbsp;&nbsp;&nbsp;| **desplazamiento** : *offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDMACROS** | **NOOLDMACROS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDSTRUCTS** | **NOOLDSTRUCTS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **proc** : *oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;| **prólogo** : *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **READONLY** | **NOREADONLY**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ámbito** | sin **ámbito**\
&nbsp;&nbsp;&nbsp;&nbsp;**segmento** | : *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SETIF2** : bool

\ *optionList*
&nbsp;&nbsp;&nbsp;&nbsp;*optionItem* | *optionList* , ⟦;; ⟧ *optionItem*

\ *optText*
&nbsp;&nbsp;&nbsp;&nbsp;, *textItem*

\ *orOp*
&nbsp;&nbsp;&nbsp;&nbsp;**o** | **XOR**

\ *oVisibility*
&nbsp;&nbsp;&nbsp;&nbsp;**público** | **privado** | **exportación**

\ *pageDir*
&nbsp;&nbsp;&nbsp;&nbsp;**Página** ⟦ *pageExpr* ⟧;;

\ *pageExpr*
&nbsp;&nbsp;&nbsp;&nbsp;\+ | ⟦ *pageLength* ⟧ ⟦, *PageWidth* ⟧

\ *pageLength*
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

\ *PageWidth*
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

\ *PARM*
&nbsp;&nbsp;&nbsp;&nbsp;*parmId* ⟦: *qualifiedType* ⟧ | *parmId* ⟦ *constExpr* ⟧ ⟦: *qualifiedType* ⟧

\ *parmId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *listadeparámetros*
&nbsp;&nbsp;&nbsp;&nbsp;*parm* | *listadeparámetros* , ⟦;; ⟧ *PARM*

\ *parmType*
&nbsp;&nbsp;&nbsp;&nbsp;**req** | = *textLiteral* | **vararg**

\ *pOptions*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Distance* ⟧ ⟦ *LangType* ⟧ ⟦ *oVisibility* ⟧

\ *principal*
&nbsp;&nbsp;&nbsp;&nbsp;*expr* *BinaryOp* *expr* | *flagName* | *expr*

\ *procDir*
&nbsp;&nbsp;&nbsp;&nbsp; **procedimiento** procId\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *pOptions* ⟧ ⟦ < *macroArgList* > ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *usesRegs* ⟧ ⟦ *procParmList* ⟧

\ del *procesador*
&nbsp;&nbsp;&nbsp;&nbsp;|. 386 |. 386p |. 486 |. 486P \
&nbsp;&nbsp;&nbsp;&nbsp;|. 586 |. 586P |. 686 |. 686P |. 387

\ *processorDir*
&nbsp;&nbsp;&nbsp;*procesador* de &nbsp;;; \
&nbsp;&nbsp;&nbsp;&nbsp;*coprocesador* | ;

\ *procId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *procItem*
&nbsp;&nbsp;&nbsp;&nbsp;*instrPrefix* | *dataDir* | *labelDir* | *offsetDir* | *generalDir*

\ *procParmList*
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *listadeparámetros* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *parmId* : vararg ⟧

\ *protoArg*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧: *qualifiedType*

\ *protoArgList*
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *protoList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ ⟦ *ID* ⟧: vararg ⟧

\ *protoList*
&nbsp;&nbsp;&nbsp;&nbsp;*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *protoList* , ⟦;; ⟧ *protoArg*

\ *protoSpec*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Distance* ⟧ ⟦ *LangType* ⟧ ⟦ *protoArgList* ⟧ | *typeId*

\ *protoTypeDir*
&nbsp;&nbsp;&nbsp;&nbsp;*ID* **proto** *protoSpec*

\ *pubDef*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧

\ *publicDir*
&nbsp;&nbsp;&nbsp;&nbsp; *pubList* público;;

\ *pubList*
&nbsp;&nbsp;&nbsp;&nbsp;*pubDef* | *pubList* , ⟦;; ⟧ *pubDef*

\ *purgeDir*
&nbsp;&nbsp;&nbsp;&nbsp;**purga** *macroIdList*

\ *qualifiedType*
&nbsp;&nbsp;&nbsp;&nbsp;*tipo* | ⟦ *Distance* ⟧ **ptr** ⟦ *qualifiedType* ⟧

*calificador*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **proto** *protoSpec*

\ de *comillas*
&nbsp;&nbsp;&nbsp;&nbsp;"|"

\ *qwordRegister*
&nbsp;&nbsp;&nbsp;&nbsp;RAX | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R9 | R10 | R11 | R12 | R13 | R14 | R15

\ *radixDir*
&nbsp;&nbsp;&nbsp;&nbsp; **. BASE** *constExpr* ;;

\ *radixOverride*
&nbsp;&nbsp;&nbsp;&nbsp;h | o | p | t | s | H | O | P | T | Sí

\ *recordConst*
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* { *oldRecordFieldList* } | *recordTag* < *oldRecordFieldList* >

\ *recordDir*
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* **registro** *bitDefList* ;;

\ *recordFieldList*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* | *recordFieldList* , ⟦;; ⟧ ⟦ *constExpr* ⟧

\ *recordInstance*
 {⟦;; ⟧ *recordFieldList* ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| < *oldRecordFieldList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *recordInstance* )

\ *recordInstList*
&nbsp;&nbsp;&nbsp;&nbsp;*recordInstance* | *recordInstList* , ⟦;; ⟧ *recordInstance*

\ *recordTag*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

*registrar*\
&nbsp;&nbsp;&nbsp;&nbsp;*specialRegister* | *gpRegister* | *byteRegister* | *qwordRegister* |  *fpuRegister* | *SIMDRegister* | *segmentRegister*

\ *regList*
&nbsp;&nbsp;&nbsp;&nbsp;*registrar* | *regList*

\ *relOp*
&nbsp;&nbsp;&nbsp;&nbsp;EQ | NE | LT | LE | GT | GE

\ *repeatBlock*
&nbsp;&nbsp;&nbsp;&nbsp; **. REPEAT** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;; untilDir ;;

\ *repeatDir*
&nbsp;&nbsp;&nbsp;&nbsp;**repetir** | **REPT**

\ *scalarInstList*
&nbsp;&nbsp;&nbsp;&nbsp;*initValue* | *scalarInstList* , ⟦;; ⟧ *initValue*

\ *segAlign*
&nbsp;&nbsp;&nbsp;&nbsp;**BYTE** | **WORD** | **DWORD** |  **Página** | 

\ *segAttrib*
&nbsp;&nbsp;&nbsp;&nbsp;**pila** de | **públicas** |  | de **memoria** **común** | **en** *constExpr* | **privado**

\ *segDir*
&nbsp;&nbsp;&nbsp;&nbsp; **.** \ de código
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.** \ de datos
&nbsp;&nbsp;&nbsp;&nbsp;|   **. ¿DATOS?** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ CONST**
&nbsp;&nbsp;&nbsp;&nbsp;|  **. FARDATA**⟦ *segId* ⟧
&nbsp;&nbsp;&nbsp;&nbsp;|   **. FARDATA?** ⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. STACK** ⟦ *constExpr* ⟧

\ *segId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *segIdList*
&nbsp;&nbsp;&nbsp;&nbsp;*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segIdList* , *segId*

\ *segmentDef*
&nbsp;&nbsp;&nbsp;&nbsp;*segmentDir* ⟦ *inSegDirList* ⟧ *endsDir* | *simpleSegDir* ⟦ *inSegDirList* *⟧ ⟦ endsDir ⟧*

\ *segmentDir*
&nbsp;&nbsp;&nbsp;&nbsp;*segId* **Segment** ⟦ *segOptionList* ⟧;;

\ *segmentRegister*
&nbsp;&nbsp;&nbsp;&nbsp;**CS** | **DS** | **ES** | **FS** | **GS** | **SS**

\ *segOption*
&nbsp;&nbsp;&nbsp;&nbsp;*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| *className*

\ *segOptionList*
&nbsp;&nbsp;&nbsp;&nbsp;*segOption* | *segOptionList* *segOption*

\ *segOrderDir*
&nbsp;&nbsp;&nbsp;&nbsp; **.**  | alfa **. SEQ** |  **. DOSSEG (**  | **dosseg (**

\ *segRO*
&nbsp;&nbsp;&nbsp;&nbsp;**ReadOnly**

\ *segSize*
&nbsp;&nbsp;&nbsp;&nbsp;**USE16** | **USE32** | **plano**

\ *shiftOp*
&nbsp;&nbsp;&nbsp;&nbsp;**SHR** | **SHL**

*firmar*\
 - | +

\ *simdRegister*
&nbsp;&nbsp;&nbsp;&nbsp;MM0 | MM1 | MM2 | MM3 | MM4 | MM5 | MM6 | MM7 | xmmRegister | YMM0 | YMM1 | YMM2 | YMM3 | YMM4 | YMM5 | YMM6 | YMM7 | YMM8 | YMM9 | YMM10 | YMM11 | YMM12 | YMM13 | YMM14 | YMM15

\ *simpleExpr*
 ( *cExpr* ) | *principal* de

\ *simpleSegDir*
&nbsp;&nbsp;&nbsp;&nbsp;*segDir* ;;

\ *sizeArg*
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *tipo* | *E10*

\ *specialChars*
 : | . | ⟦ | ⟧ | ( | ) | < | > | { | } \
&nbsp;&nbsp;&nbsp;&nbsp;| + | - | / | * | & | % | !\
&nbsp;&nbsp;&nbsp;&nbsp;| ' | \ | = | ; | , | "\
&nbsp;&nbsp;&nbsp;&nbsp;| *whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;| *endOfLine*

\ *specialRegister*
&nbsp;&nbsp;&nbsp;&nbsp;CR0 | CR2 | CR3 | DR0 | DR1 | DR2 | DR3 | DR6 | DR7 | TR3 | TR4 | TR5 | TR6 | TR7

\ *stackOption*
&nbsp;&nbsp;&nbsp;&nbsp;**NEARSTACK** | **FARSTACK**

\ *startupDir*
&nbsp;&nbsp;&nbsp;&nbsp; **. Inicio** ;;

\ *stext*
&nbsp;&nbsp;&nbsp;&nbsp;*stringChar* | *stext* *stringChar*

*string*\
&nbsp;&nbsp;&nbsp;&nbsp;*Quote* ⟦ *stext* ⟧ *Quote*

\ *stringChar*
&nbsp;&nbsp;&nbsp;&nbsp;*comilla* de *comilla* | Cualquier carácter excepto la comilla.

\ *structBody*
&nbsp;&nbsp;&nbsp;&nbsp;*structItem* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *structBody* *structItem* ;;

\ *structDir*
&nbsp;&nbsp;&nbsp;&nbsp;*structTag* *structHdr* ⟦ *fieldAlign* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, no es **único** ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;**finaliza** ;;

\ *structHdr*
&nbsp;&nbsp;&nbsp;&nbsp;**STRUC** | **struct** | **Union**

\ *structInstance*
 < ⟦ *fieldInitList* ⟧ > \
&nbsp;&nbsp;&nbsp;&nbsp;| {⟦;; ⟧ ⟦ *fieldInitList* ⟧ ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *structInstList* ) \

\ *structInstList*
&nbsp;&nbsp;&nbsp;&nbsp;*structInstance* | *structInstList* , ⟦;; ⟧ *structInstance*

\ *structItem*
&nbsp;&nbsp;&nbsp;&nbsp;*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *nestedStruct*

\ *structTag*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

*término*\
&nbsp;&nbsp;&nbsp;&nbsp;*simpleExpr* |! *simpleExpr*

*text*\
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* | carácter de *texto* |! *texto* de carácter | *carácter* |! *carácter*

\ *textDir*
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *textMacroDir* ;;

\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* | *textMacroId* | % *constExpr*

\ *textLen*
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

\ *textList*
&nbsp;&nbsp;&nbsp;&nbsp;*textItem* | *textList* , ⟦;; ⟧ *textItem*

\ *textLiteral*
&nbsp;&nbsp;&nbsp;&nbsp;< *texto* >;;

\ *textMacroDir*
&nbsp;&nbsp;&nbsp;&nbsp;**catstr (** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **TEXTEQU** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **sizestr (** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **substr** *textItem* , *textStart* ⟦, *textLen* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **instr** ⟦ *TextStart* , ⟧ *textItem* , *textItem*

\ *textMacroId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *textStart*
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

\ *titleDir*
&nbsp;&nbsp;&nbsp;&nbsp;*titleType* *arbitraryText* ;;

\ *titleType*
&nbsp;&nbsp;&nbsp;&nbsp;**título** | **subtítulo** | **SUBTTL**

*type*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *distance*\
&nbsp;&nbsp;&nbsp;&nbsp;| *datatype*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId*

\ *typedefDir*
calificador de **definición** de tipo &nbsp;&nbsp;&nbsp;&nbsp;*typeId*

\ *typeId*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *unionTag*
&nbsp;&nbsp;&nbsp;*id* &nbsp;

\ *untilDir*
&nbsp;&nbsp;&nbsp;&nbsp; **. HASTA** *cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. UNTILCXZ** ⟦ *cxzExpr* ⟧;;

\ *usesRegs*
&nbsp;&nbsp;&nbsp;&nbsp;**usa** *regList*

\ *whileBlock*
&nbsp;&nbsp;&nbsp;&nbsp; **. MIENTRAS**\
&nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. ENDW**

\ *whiteSpaceCharacter*
&nbsp;&nbsp;&nbsp;&nbsp;ASCII 8, 9, 11 – 13, 26, 32

\ *xmmRegister*
&nbsp;&nbsp;&nbsp;&nbsp;XMM0 | XMM1 | XMM2 | XMM3 | XMM4 | XMM5 | XMM6 | XMM7 | XMM8 | XMM9 | XMM10 | XMM11 | XMM12 | XMM13 | XMM14 | XMM15\

