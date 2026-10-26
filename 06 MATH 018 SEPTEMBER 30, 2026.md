# MATH 018 Online Class: Unifying Theorem, Permutations & Determinants (Transcript)
Instructor: professor. Recording is about 2 hr 59 min long. The transcript is in Taglish, as spoken (auto-transcribed with Whisper large-v3-turbo; expect occasional mishearings, e.g. "add" where "odd" was said).

## Topics covered
- Recap: non-singular matrices (A inverse exists), finding A⁻¹ by running Gauss-Jordan on [A | I], and the 3 types of elementary matrices (row interchange, row scaling, row addition) with their inverses
- Proof of the unifying theorem (5 equivalent statements) as a full circle 1 ⇒ 2 ⇒ 3 ⇒ 4 ⇒ 5 ⇒ 1. Includes the indirect proof (proof by contradiction) of 3 ⇒ 4, explained with the "walang kabit ang asawa ko" story
- Example: proving a 2×2 matrix is non-singular and writing it as a product of elementary matrices. Student caught a typo on the slide: E21(−1) should be E21(−2), because the entry being eliminated is the 2. Analogy: elementary matrices are like primes
- Long Exam 1 is not next week, probably about two weeks from now, to line up with the other CS sections
- Permutations: bijections X → X, the set S_n, and n! elements (the 3·2·1 count). Job-assignment analogy
- Inversions: arrows that cross, counted quickly as "smaller numbers to the right". Even/odd parity. The identity permutation is even. Half of S_n is even and half is odd. Swapping two entries flips the parity. Notation (−1)^π
- Definition of the determinant: a sum over S_n of signed products, taking one entry from each row with no repeated column (n! terms)
- 2×2 formula. 3×3 "down-down-down, up-up-up" mnemonic; the example comes out 0 because row 3 = row 1 + row 2 (redundant information). numpy `np.linalg.det` and calculator check
- Warning: the arrow method does NOT work for 4×4 and up (it gives only 8 of the 24 terms)
- 5×5 sparse example: only one non-zero term (permutation 2,5,1,4,3, odd). ⚠ In class he said **−196**, but his own product 1·2·3·4·7 = 168, so the determinant should be **−168** (numpy agrees). He multiplied 28×7 instead of 24×7
- Geometry: |det| is the area of a parallelogram (2×2), the volume of a parallelepiped (3×3), and the n-dimensional signed volume in general
- Triangular and diagonal matrices: det = product of the main diagonal. det(I) = 1. A zero row or column gives det = 0
- Break, about 1:56 to 2:02 (the recording is silent)
- Properties: det(Aᵀ) = det(A), and the duality of rows and columns. Type 1 (swap) flips the sign. Two identical rows or columns give 0 (6×6 example, student). Type 2 (scale a row by c) multiplies det by c, so det(cA) = cⁿ det(A). Trick question: row 3 = −2 × row 1, so det = 0 (student). Type 3 (row addition) leaves det unchanged
- Method: reduce to upper triangular with row operations. 4×4 worked example: the first attempt gave −364 vs the calculator's −160; Gemini found the error in step 2, and the redo gives −160
- New 6th statement of the unifying theorem (added this lesson): A is non-singular ⇔ det(A) ≠ 0. The proof comes next meeting. Progress: "6 out of 20" statements
- Next meeting: a second method for determinants, combined with row reduction. The slide problem is assignment, to be checked next meeting

## Transcript
**[00:04]** Okay, so the session is now recorded. So bago tayo magsimula ng lesson, i-recall muna natin yung nangyari last time, no? So last time, pinag-usapan natin yung or na-i-define natin. Kailan natin sinasabi ng isang matrix over a field of scalars is singular, ay, is non-singular. Ang desirable property guys, yung non-singular, na yung hindi natin masyadong gusto yung singular. Na bakit gusto natin na ang matrix ay non-singular?

**[00:47]** As a basic property, pag sinabing ng singular, yung A inverse o yung inverse ng matrix ay nage-exist, no?

**[01:00]** Anong ibig sabihin ng A inverse? Yung A inverse may property siya na kapag minultiply si A, so either from the left or from the right, ang lumalabas na product is simply the identity matrix. Now, ang reason kaya natin gusto na ang matrix ay non-singular at may inverse siya kasi gusto natin Hindi, yung mga matrices na ito, when you view them as transformations, parang yung nakaraang motivation natin yung meron kang vectors containing information and then ang ginawa natin, in-encrypt natin using a non-singular matrix. Kasi kapag yung matrix na, yung matrix encryption ay non-singular, pwede mong i-reverse yung effect.

**[01:51]** So meaning to say, kapag may vector x ka na in-encrypt ng A to become the vector y, ang mangyayari kung si A ay non-singular, yung x ay mararecover mo by simply multiplying the inverse of a to the vector y. So basically, yun yung ating motivation for having or for studying non-singular matrices. Naaalala nyo ba ito? Maliban doon, tinukoy natin last time yung, ano ba yung mga tinukoy natin? Kung paano, kumpitin yung inverse na yan whenever A is non-singular. Sabi natin, si A ay, kapag si A ay non-singular, no, yung RREF niya, ay, dapat, identity matrix. Do you recall this?

**[02:46]** Furthermore, kung sakali mang yung method natin to get the inverse, kung si AI non-singular, kapag kinabitan mo siya ng identity matrix, nag-augment ka ng identity matrix sa kanan niya of the same size, and you run the Gauss-Jordan algorithm, and eventually yung matrix, syempre nga, ang RREF ng AI identity, yung portion na ito sa kaliwa, magiging IN, at kung sakali mang may lumabas na matrix B dun sa kanan, mag-follow na yung B na yun actually was the inverse of A. So more or less parang ito yung method natin on how to look for the inverse. And if you look at this closely, pag meron kang AX equals Y, Do you recall na para ka lang nagsosolve ng isa ang linear system, no?

**[03:45]** In fact, kapag meron kang linear system na AX equals Y, tapos A ay non-singular, ito yung formula para sa iyong unique solution. You just multiply the inverse of A to the right, from the left of the vector y. Do you recall all of this? At yung ginawa natin last time, no? Maliban dyan, na-i-define na natin yung mga tinatawag na elementary matrices, no? Ano nga yung sabihin ng elementary matrix? Pag sinabing elementary matrix, nagperform ka sa identity matrix ng isang elementary row operation, ang lalabas ay elementary matrix. Ito yung tag nating elementary matrix.

**[04:34]** Ano natutuhan natin last time? Tingnan nga natin. Ayan. Na ang mga elementary matrices, if you look at them closely, may tatlong uri, no? Kasi kapag ang pinerform mo ay row interchange, pwede rin row scaling kapag nag-scale ka ng isang row by a non-zero scalar o yung row addition, yung nag-add ka ng isang row to a multiple of another. If you do that, tatlo yung uri rin ng elementary matrices, we found out na itong mga elementary matrices na to are non-singular. In fact, ang inverse nila is an elementary matrix one more time. of the same type. So, pag type 1, type 1 ang inverse. Pag type 2, in fact, ang mga type 1, as you can tell, self-inverse sila, no?

**[05:25]** Pero ang type 2, hindi. Pag nag-multiply ka ng alpha to undo the effect, kailangan mo mag-multiply back ng 1 over alpha, o yung inverse reciprocal ng alpha. And when you add row i with alpha times row j to undo that, the effect, ang kailangan mong gawin, i-add ulit yung row i sa minus alpha times row j. So para mo makancel yung effect nung addition ng alpha times row j. So, susubtract mo yung alpha times row j. Does that make sense? Nag-make sense ba yung, ano, yung, yung nakikita nyo dito sa screen, na? Yung make sense naman ba para ma-undo? So, ito yung ating natutuhan.

**[06:12]** Lahat ng mga elementary matrices ay non-singular and ang inverse nila is again an elementary matrix of the same type. Now, they were called elementary matrices guys kasi ano nga sabi ko? Maliban sa napaka basic ng itsura nila. ang aking motivation last time was, sila yung mga building blocks ng mga non-singular matrices. Sila yung mga basic examples ng non-singular matrices and it turns out that according to the unifying theorem, kasi these statements are equivalent daw, sabi niyo. So, yung sabihin, pag yung isa dito ay true, lahat yan ay true. Pag yung isa dito ay false, lahat sila ay false.

**[07:00]** Kaya kapag si A ay non-singular, ang totoo daw, si A ay product ng elementary matrices or masasulat mo siya as a product of elementary matrices. Okay, so are you ready to listen kung bakit naging equivalent yung limang statements na to? Okay, so babasahin ko isa-isa and I will try to recall, no? Kung anong ibig sabihin yung bawat statement, no? Sige. Yung statement number one, the fact that matrix A is non-singular means, simple lang ang ibig sabihin nun, nage-exist yung A inverse. Meron kang A inverse, okay? Pangalawa, I think... napaliwanag ko na to, kapag si A ay non-singular kasi, yung linear system na ax equals b, masosolve mo uniquely by multiplying a inverse, diba?

**[07:53]** Si x mo dito is actually a inverse times b. Actually, nagawa na natin siya in last week. And in particular guys, pag itong b na ito, ginawa mong zero, magiging homogenous siya ngayon. At kapag homogenous yan, trivial solution lang ang meron kasi kapag ang ax ay zero, ang x mo ay a inverse times zero. But regardless of a inverse, this product is just the zero vector. trivial solution. And we also found out last time na kapag si AI non-singular, di ba ang RREFI identity? Siguro ang ngaalamin natin bakit kapag si AI non-singular, bakit siya product ng elementary matrices?

**[08:40]** So let me... guide you through the proof of this. Kasi this is so important kasi unifying theorem siya yun. Kung baga, this is what's holding our course in one place. Kasi marami tayong topics na maaaral in the future but... itong unifying theorem nito will keep on appearing from time to time and from time to time mag-a-add tayo ng more and more statements to this. Ibig sabihin, this is what's holding the subject in one piece. Do you understand? Kaya nga siya unifying theorem. Did you understand? At pag itong unifying theorem na ito, naging 20 statements na ibig sabihin nun matatapos na yung semester.

**[09:27]** At the end of the semester, this becomes a list of 20 equivalent statements, guys. 20 nga ba? I forgot, but basically, yun yung aking plan. Okay? So, how do we prove that a set of statements are actually equivalent? How do we write a proof or how do mathematicians do that? Basically, kasi kapag dalawang statement lang, let's say statement P and statement Q, if you want to prove that they are equivalent, we try to show that they imply one another. Now, meaning P implies Q and Q implies P. Dalaway ipoprove mo. Pero kapag limang statements ang pinuprove mo equivalent with transitive property in mind, alam ninyo, ang strategy, one strategy is to prove that 1 implies 2, 2 implies 3, 3 implies 4, 4 implies 5, at pag ang 5, in-imply niya si 1, would you agree with me na tapos na tayo? or equivalent na sila lahat, kasi you just have made a full circle. So, si 4 ngayon, iniimply si 1.

**[10:42]** Di-understand kasi kapag ang P implies Q, Q implies R, did you remember si P implies R? Anong tawag nyo dito sa argument na ito. You call this the hypothetical syllogism. Do you recall this? From logic, no? Kaya kapag napatunayan mo itong full circle na ito, full circle of implications na ito. you can be able to say that these statements are equivalent. In fact, this is exactly what we're trying to do. So, actually, this part, the fact that one implies two is already done. Ginawa ko na siya last meeting. If you recall. Now, kapag si A ay non-singular, napatunayan natin na yung ax equals b, kahit ano yung b, ay may unique solution.

**[11:36]** In fact, ang solution ay a inverse times b. Did you recall that? Okay? Ito naman. Assuming statement 2, bakit totoo yung statement 3? Actually, this is finished. Ang gagawin nyo lang, assuming 2,

**[11:56]** you just take the vector B in particular as the zero vector. Kapag ginawa mong zero vector yung B dito, pagiging homogenous siya. And in this case guys, di ba? yung x mo, according to our, ah, theorem last time. May unique solution ito. Diba?

**[12:21]** Eh kaya lang, alam natin from a previous lesson na, from the previous lesson na kapag homogenous ang linear system, there is always an automatic solution. ang automatic solution natin yung trivial solution. So, kung may unique solution ka at automatic solution ng trivial solution, ibig sabihin nun, this linear system only has the trivial solution and nothing else. Did you understand the logic guys? Naunawaan ninyo? O, di ba? So that's 2 implying statement number 3. So this time, siguro ang ating i-justify ayun 3 implies 4, okay?

**[13:08]** So here, we are under the assumption that statement 3 holds, meaning to say, hindi ko na isusulat ulit, itong AX equal 0, assuming it only has the trivial solution, guys. What we're trying to show here is that the RREF of A is basically the identity matrix, okay? Bakit kaya? Alright, so ganito. Ang strategy ng proof dito, kasi hindi mo naman pa pwedeng computein yung RREF directly, kasi wala namang entries ka nakikita kay A na, so we cannot compute it directly. So, etong mga ganitong klaseng proof, no?

**[13:55]** Kailangan natin itong gawin indirectly. When you say indirectly, sinusuppose natin yung negation ng conclusion. Kunwari, hindi identity yung RREF ni A, anong mangyayari? Ano bang mangyayari pag hindi identity ang RREF? Parang ano yan, ganito. Halimbawa, diba, nag-argue ko yung magkaibigan. Let's say, kini-claim mo na Hindi totoo yan. Ang ano, ah, walang kabit ang asawa ko. Ayon, ganyan. Kunwari, naniniwala ka sa asawa mo, nagpapabudol ka sa asawa mo. Kunwari, sabi ng asawa, wala siyang kabit. Tapos, may nagsabi sa'yo, may kabit yung asawa mo, eh hindi ka naniniwala. Sabi mo, ah, ah, Hindi totoo yan, walang kabit ang asawa ko.

**[14:40]** Anong gagawin mo para patunayan yan? Sabihin mo, o sabihin na natin may kabit siya. Do you understand the point? Sinusuppose natin yung negation and then if we can come up with something absurd, ibig sabihin hindi totoong may kabit siya. dapat wala siyang kabit. Did you understand? Nakukuha niyo yung ano, ang tawag natin dito sa math, we call this the indirect proof. Pag indirect proof, nangangatwiran tayo, by the way na kunwari hindi totoo yung conclusion, ano bang mangyayari? If it turns out to be something absurd will happen or will be implied or will be deduced, ibig sabihin, yung sinu-post mo hindi pa pwedeng mangyari.

**[15:26]** Mapipilitang maging identity yung RREF. Did you understand? Okay? Yup, yup. Okay, sige. Ano bang mangyayari kapag hindi identity ang RREF? Ang mangyayari guys, tawagin natin B yung RREF. So walang pangalan yung RREF ni A na, let's say ang RREF niya ay B. Then, you know, isa sa mga property ng B kung hindi identity matrix ang Kasi pag-identity guys, ibig sabihin nun, lahat ng rows at lahat ng columns mo may mga pivot. Nakaayos ng maayos, right? Lahat ng rows will receive a pivot. So kapag hindi identity ang RREF mo, the only possible scenario is magkakaroon ka ng zero row.

**[16:21]** Do you agree with me?

**[16:26]** Hello? Do you agree with me? Yan yung magiging implication nun. Kung hindi identity ang RREF mo, yung RREF magkakaroon ng zero rows. At pag nagkaroon ka ng zero rows guys in the RREF, Ipig sabihin, magkakaroon ka ng column na walang pivot. And therefore, yung linear system mo magkakaroon ng free variable. Would you agree with me? Thus, the linear system Bx equals 0 shall have what? Free variables

**[17:09]** So, it has infinitely many solutions.

**[17:19]** But you know, ang sinosolve natin ay Bx equals 0. Ang original na linear system ay Ax equals 0. Eh dahil si B ay RREF lang naman ni A, ibig sabihin, sinosolve mo rin yung Ax equals 0. So, as it turns out, Si ax equals 0, this has to have infinitely many solutions again. Ah, not again. Also, did you understand? We'll have infinitely many solutions as well.

**[17:56]** Kasi pag-solve mo yung Bx equal 0, sinosolve mo din si Ax equal 0 kasi RREF ni ACB eh. Diba? Pwede bang mangyayari ito na si Ax equal 0 has infinitely many solutions? No. Kasi according to the hypothesis or the assumption, this only has that FBL solution. How can it have infinitely many solutions? It's not possible. I mean, those two things cannot happen at the same time. So, ang ibig sabihin ng symbol na yun, guys, something is wrong or there is a contradiction. Are you familiar with that symbol? If not... that's what we use. So because something absurd, well, ba't kung lagyan na ganun? Paliwanag natin, contradicting statement number 3 or the assumption.

**[18:47]** Because there's a contradiction, ibig sabihin hindi ka pwedeng, hindi identity ang RREF. So therefore, the RREF of A has to be the identity. Naintindihan nyo bakit tinawag na, what do you call this? Bakit tinawag na indirect proof? Kasi indirect siya, hindi dahil direkto natin pinakita na identity matrix yung RREF kasi we cannot do that. Ang ginawa natin, sinu-pose natin na hindi identity yung RREF if it turns or if some, if we can be able to deduce something which is a contradiction, ibig sabihin, hindi pa pwedeng mangyari yung sinopose natin.

**[19:35]** So wala tayong choice, pag hindi identity, kung di katao na ang RREF ay hindi identity, dapat ang RREF no ay identity. Are you able to follow the line of thought, o yung thought process? Sige. Naintindihan nyo? Hello? Or I proceed? Sige ah. Alright. So, buburahin ko na to muna, para mas mabilis. So, napatunayan na natin ito. Ang markahan ko, okay? Check, check, check, okay. So, ipoprove natin ngayon that 4 implies 5.

**[20:24]** Statement 4 implies statement 5. So, paano ito? So, we will assume that the RREF of A is the identity. Ang tanong, bakit si A ay product ng elementary matrices? Anong ibig sabihin? Well, ganito yan. Ano bang ibig sabihin kapag ang RREF ni A ay identity? Ibig sabihin you can perform a sequence of elementary row operations to A until it becomes the identity matrix. Do you recall the previous lesson? Sabi natin our previous quick, sabi natin, sa bawat elementary row operation na ginagawa mo, kay A, it accounts to multiplying an elementary matrix from the left. Kaya kung nakagawa ka ng K na elementary row operations, ang totoo niyan, nag-multiply ka ng K na elementary matrices sa kaliwa ng A. Do you recall that? So, imaginein mo ito yung RREF ni A.

**[21:35]** Anong mangyayari guys? Ay, sorry. Ito yung mangyayari ha. Then, there exist elementary matrices tawagin natin E1 up to EK,

**[21:57]** lahat sila N by N din, no? Such that, eto si A, pag in-apply ko si E1, sinunda ng E2, hanggang EK, ang lalabas eventually ay identity. Kuha niya? Right? Hello? Nasunda na. Okay, ganito. Anong alam natin sa mga elementary matrices? Alam natin na mga elementary matrices ay non-singular by default. We know that. So therefore, dahil ang product ng mga non-singular matrices ay non-singular, hindi ang sum, na? Ang product ng mga non-singular ay non-singular, pero kapag sum, hindi, necessarily, na? So, ibig sabihin, itong malaking block na ito, if you can see yung product na EK hanggang E1, This is non-singular as well.

**[23:02]** So meaning to say, I can multiply its inverse sa left. So para ma-isolate yung A, ang mangyayari, makukuha ko lang yung inverse na itong malaking product na ito. E identity yung nasa kanan.

**[23:21]** Okay? were you able to follow? Eh dahil nga identity yung nasa kanan, you don't really have to write it. Okay? So, may iiwan dito si A ay itong inverse na lang na ito but you know we have the shoes and socks property so we can make it into this. bumabalik na yung order na. May recall each one of this? O, ano sabi natin in the previous slide? Since each EI is elementary, then so are, or so is, It's inverse, EI inverse. Do you remember sabi ko ang inverse ng mga elementary matrices ay elementary matrix din? So lahat ito, kahit na may inverse sila, ay mga elementary matrix din.

**[24:24]** So therefore, A is a product. of elementary matrices. I was able to write A as a product of elementary matrices. Huwag kayong magalala, meron akong example mamaya. Okay? Naintindihan ninyo, bakit si A ay product ng elementary matrices? Pagkatapos, pagkatapos niyan. Pagkatapos po, tapos na yung 4 implies 5, okay? Finally, yung 5 implies 1, this is trivial. Alam niyo bakit? This is trivially true. Bakit? Kasi pag si AI... product ng elementary matrices, ang sabi natin ng mga elementary matrices ay non-singular. So, ang product ng mga non-singular ay non-singular, therefore, si A ay non-singular.

**[25:22]** Did you understand? And that completes the cycle. So, these five statements from today and onwards are equivalent to one another. So, ibig sabihin, every time or each time na narinig mo na yung isa dyan sa lima ay true, yung the other four statements will be true as well. Ang galing, no? Ibig sabihin, marami kang pwedeng masabi kapag nalaman mo na ang isang square matrix A ay non-singular. Marami siyang features. Did you understand? Dahil nakita na natin yung action yung number 2, number 3 at number 4 at yung bago sa atin yung number 5.

**[26:08]** Meron akong example dito. Sabi dito, no? Prove that this matrix A is non-singular and write it as a product of elementary matrices. Sabi nga natin kapag non-singular, mapafactor mo siya into products of elementary matrices. So let me show you how. So, paano muna ipapakita na siya yung non-singular? Well, one way to do that is to simply get the RREF. Kailangan ng RREF identity. Ang gawin natin. So, tingnan nyo. Ang first step, pwede ninyong pagpalitin yung rows 1 and 2 para yung 1 mapunta dito sa portion na ito, di ba? And then, if you recall, from this one, we are going to eliminate the two below it by applying this type three operation.

**[27:03]** P, two, one, negative one. Do you recall? Naalala? Okay, naalala yan ha? Sige. Ito yung mangyayari. Of course, the two from below is going to be eliminated and actually we are one more step, diba? Away from the end. Kasi, one na ito, so gusto mo na lang maging zero yun.

**[27:33]** Mali ba? Wait. Ay, student? Naka, ano ka? Naka-raise ng hand? Sir, may audible po? Yes, oo. Sir, yung nakalagay sa loob ng parentheses po, ah, negative ba talaga dapat yan? Hindi po ba negative ito? Kasi... Ah, thank you, student. hindi ko napansin. This is scalar, yung nasa loob ng parentheses, has to be negative 2. Kasi ang ini-eliminate natin ay 2, hindi yung 1, okay? Tama si student, that has to be negative 2, pero... yung sagot ay hindi naman magbabago, diba? Kasi ito mamumultiply by negative 2.

**[28:19]** Negative 2 plus 3 is still 1. Maybe a typing error, but anyway, I have no excuse. Ito yung negative. Thank you, student. Finally, ang gagawin ko... To eliminate this thing, gamit yung pivot na ito, I have to use E1 to negative 1. Ibig sabihin, susubtract mo no, row 1 minus row 2. Yan ang meaning nyan eh. Diba? So finally, in the end, what happened is that, um, naging identity na, So therefore, A is non-singular. Okay? Ang tanong, paano naman natin isusulat si A as a product of elementary matrix? Ay, negative to ito, ha? So let me now show you kung paano ginagawa yan, guys.

**[29:09]** Ganito. If you follow the proof, yung proof natin kanina, if you follow it, eto si A natin. Sulat ko lang si A. Ang unang elementary row operation na in-apply natin ay E12 followed by this, followed by this. So, ang gagawin ko, yung corresponding elementary matrix, imumultiply ko sa kaliwa ng paisa-isa. So, meaning to say, lalagay ko dito, E1, 2, E2, 1, negative 2. Are you following along? Finally, E1, 2, negative 1. nakasunod?

**[29:56]** Anong lalabas dapat? Ang lalabas ay identity 2 by 2, kasi yun yung naging sagot sa dulo. Okay? According to the proof, yung A dito has to be the inverse of this product. Nakukuni mo yung product na ito and

**[30:17]** then get its inverse. Yan yung a. But, you know, when you, when you take the inverse, it has to be e12 inverse, e21 negative 2 inverse, and e12 negative 1. inverse. In the previous lesson, or last week, tinuruan ko kayo kung anong inverse ng mga elementary matrices na ito, right? Tama ba? Iayos ko ito para may space tayo. There you go. Sa pag-type 1 ang matrix, remember it's basically self-inverse.

**[31:03]** So yung E1 to inverse is just E1 to one more time. Yung E2 1 negative 2, pag type 3, you just change the sign. From negative 2 yung nasa loob, magiging positive 2. May recall that? At yung negative 1 mo, dun sa E1 to negative 1, magiging positive 1 lang. And you're basically done. So kung gusto mong makita, kung ano yung tura ng mga matrices na ito, pag simula ka sa identity, i-apply mo yung mga operations na ito. Ano ba, E1 to, eto po siya. Ano yun? 0110. Pinagpalit mo yung first row at second row ng identity, okay?

**[31:48]** Pag type 3, i-apply mo yung type 3 operation na to sa identity, pero ang shortcut kapag type 3, tinuruan ko kay last time, pag type 3, lalagay mo lang yung dalawang 1 dito, tapos... Sa 2, 1 position, maglalagay ka lang ng 2. 2, 1, so dito mo ilalagay yung 2, and then this is going to be 0. Yun yung meaning nung E2, 1, parenthesis 2. And then finally, yung E1, 2, parenthesis 1, identity sya to sa 1, 2 position may element or entry na 1. So in other words, that's A as a product of elementary matrices. Did you understand? If you want to confirm if this is correct, so pwede nyo i-multiply, no? Eh pwede natin i-check. i-multiply natin yung mga matrices na yan, and let's see if the resulting product is basically A.

**[32:45]** So lalagay ko dito yung 0, 1, 1, 0. Lalagay ko dito yung 1, 0, 2, 1, and then finally lalagay ko dito yung 1, 1, 0, 1. Do you understand bakit ganyan yung aking table? Umultiply ko kasi yung tatlo. Sige, multiply natin ha? Okay, so munang dalawa. First row, first column, going to be two, first row, first column, one, first row, second row, first column, 1, second row, second column, 0. So ito naman ngayon, yung resulting product, i-multiply natin dito. So again, first row, first column, that's 2.

**[33:32]** First row, second column, it's 3. Second row, first column, it's 1. second row, second column is again 1. Do you recognize that this matrix is basically A? Diba? Sa baligtad na. So we were now able to factor A as a product of elementary matrices knowing the fact that it is non-singular. Did you understand? The fact that it is non-singular is a guarantee na maisusulat mo si A, or mapafactor mo si A into elementary parts, o yung tinatawag natin mga elementary. matrices. Kaya nga sabi ko sa inyo, parang ang mga elementary matrices, parang yung mga prime numbers nung maliliit kayo, diba?

**[34:22]** Lahat kasi ng mga integers na hindi zero, na positive, greater than 1, halimbawa, 40. Mga susulat mo yan as 2 times 2 times 2 times 2 times 2 times 5. Product siya ng apat na prime numbers. In this case, AA non-singular, plus product siya ng tatlong elementary matrices. Did you understand? Yung example na ito? How it exhibits one of the proofs na nakita ninyo, no? In actual. Okay. So, if that is the case, meron ba kayong questions before I proceed with the next lesson? Guys, ano kayong tanong?

**[35:15]** Okay. So, nandito na tayo sa huling lesson. na, covered ng, ah, wait lang ah, kunin ko lang yung slide kasi wala akong, hindi ko na ilagay pa yung slide dito, saglit lang,

**[35:42]** ay na, wala pala yung slide ko no, hindi ko pala na, na i-ano, na i-share, na-unshare ko pala, wait a minute,

**[36:00]** okay. Nakikita nyo na ba ulit yung aking slide? Or not? Nakikita, pero ba't ako hindi? Ayan. Anyway, we are now down to the last lesson to be included as part of long exam number one. Don't worry, next meeting will not be your long exam 1, baka sa susunod.

**[36:31]** Nararamdaman ko na na, I mean, next week hindi pa, okay ba? Next week hindi pa ang pakiramdam ko sa susunod. Anong date yun? Can you help me, ano, find the correct date? Anong wala kong calendar on my side?

**[36:58]** So, kung hindi next week, definitely hindi next week, kasi, you know, Ganito, ang reason ko kaya hindi next week. Sa totoo lang, kaya kong madaliin yung lesson na ito para next week na yung long exam. Ang, I'll be honest with you, the reason why I don't want to hold my long exam next week, kasi, ano ba reason ko? Yung other CS students ko ay malayo. Medyo nauuna kayo. Medyo nauuna kayo. So, ayoko kasi na magkakahiwalay yung linggo kung kailan kayo mag-e-exam. Gusto ko kung mag-e-exam kayo sabay-sabay ng linggo. Lahat ng mga CS students. Yun yung aking... plan. Okay? So, wala naman tayong minamadali at wala naman tayong gustong patunayan sa mundo. So, okay lang yun ah. Ituloy natin yung exam mga two weeks from now. At the same time, parang meron pa kayong time to actually review.

**[38:03]** Okay? Alright? Pwede na makinig? Ready na? Ready na? Okay. Ang next lesson ay tungkol sa determinant. Naalala niyo yung unifying theorem? The unifying theorem allows us to talk about non-singular matrices. Tapos, in a different, in different flavors, diba? Iba-ibang flavor ng non-singularity tungkol sa linear system, tungkol sa RREF, tungkol sa elementary matrices, diba? Yan. Dadagdagan natin siya in this lesson. So, magkakaroon kayo ng pang-anim na statement. Kasi, you know, Minsan, yung pag-RREF, it takes a lot of time.

**[38:52]** Do you agree with me? Kasi diba, to know if a matrix has an inverse, kailangan mong gawin yung RREF. And you know, doing RREF can take a lot of time, I understand, no? This lesson will give you an alternative. I'm not saying that this is easier all the time, wala akong ganung claim, but at least you have an option. Alam nyo ba tinawag na determinants ito? Kasi ang mga determinants, they determine if a given matrix is non-singular or singular, okay? it determines if a given matrix is non-singular or singular. Yun yung reason kaya ang tawag dito sa lesson na ito ay determinant. So, but before we talk about determinant, there are some few things that you must know to be able to understand.

**[39:45]** Ang una dun sa listahan ay yung concept nung tinatawag natin permutation. Have you heard about permutations before in other subjects? Sino nakakaalala na ito? Ayan, nakapuso. So narinig nyo na ito. Basically, when you say permutation, ang pinakamalapit ng English word ay arrangement of things. So halimbawa may limang bata. magpapapit, let's say, tawagin natin student 1, student 2, student 3, student 4, student 5. They can, let's say, magpo-post sila for a photo. So this arrangement is fine. That's a permutation of 1, 2, 3, 4, and 5. But you know, you can rearrange them in some other ways.

**[40:30]** For example, 2, 3, 5, 1, 4. That's also a permutation. Imaginin mo na parang si student 1 dumipat dun sa pang-apat, student 2. Did you understand? So parang nagkaroon ng rearrangement. So that's also a permutation. But you know, as we permute, mapapansin ninyo, parang ang nangyari talaga ay parang nagpalit-palitan sila ng upuan, no? So parang merong function. Kaya nga sa MATH, the way we would like to define a permutation is to use functions or In this case, bijection. So let me read the definition for you, okay? So meron kang set x, yung set x, ang laman na ito kahit na ano ulit, it doesn't have to have numbers in it, no? Lagay mo yung nanay mong blue, yung tatay mong red, lagay mo doon sa x. Bahala ko, yung ating mong attribute na lagay mo sa x, I don't care.

**[41:33]** Basta kahit na anong nasa x, wala tayong pake. Yun yung set na pinipermute natin. So basically, when we speak of a permutation on the set x, anong meaning natin? We mean any bijection, from x to x. Anong ibig sabihin ng bijection? Okay, mag-alala, yung salitang bijection is just a fancy term for a function that is 1 to 1 and onto. Anong ibig sabihin nun? So halimbawa, ang x natin, tatlo ang laman. Mama mong blue, tatay mong red, tsaka ate mong green. O kung nga na yan, yan silang tatlo na si 1, 2 at 3.

**[42:19]** Paano ka gagawa ng 1 to 1 and onto functions from x to x? Para kang gagawa ng matching na 1, 2, 3, 1, 2, 3. Gagawa ka ng mga arrows that maps the left element to the right element so that, ang rule, walang dalawang element ang mamamap sa iisang element. Tapos lahat sila ay may kanya-kanyang kapartner after the mapping. Yun yung ibig sabihin ng 1 to 1 at onto. Pag sinabing 1 to 1, walang dalawa ang maimamap sa iisa. Pag sinabing on 2, lahat sila may kanya-kanyang kapartner after the mapping. The meaning to say, halimbawa, si 1, pag minap ko yan sa 2, bawal ko nang imap si 2 sa 2. Pwede sa 1 or sa 3. Pero pag minap ko na siya sa 3, Si 3 wala nang ibang choice but to be mapped to 1.

**[43:12]** I understand? So we call this mapping or this bijection as the permutation. If you think of pi as a function, ibig sabihin si pi minamap si 1 kay 2 minamap ni pi si 2 kay 3, at si 3 ay minamap ni pi kapunta kay 1, no? Using our function notation, pi of 1 is 2, pi of 2 is 3, pi of 3 is 1. Ang ginagamit ko lang na symbol, as you can tell, no? ay 1, 2, 3, hanggang n. But in reality, itong 1, 2, 3, hanggang n, it doesn't have to be numbers. They are just set of symbols. Kung baga, gusto ko lang bigyan kayo ng set na merong n elements. I don't want you to interpret this as actual numbers, okay?

**[44:01]** They can represent any objects. So yung x mo, it can be any set with n elements. The reality is that the elements that you see in x are not necessarily numbers. Numbers are just convenient way to represent things but they are not really numbers in this case. kumbaga yung sumbrero na ginagamit nila is not really, not exactly as numbers, no? They are as numbers but general. Okay? If you construct all the permutations on X, the collection the collection of all such permutation will be denoted by the symbol S sub n, okay?

**[44:47]** Bakit S? It comes from the word symmetric. I cannot explain for now bakit symmetric na. But anyway, yan yung notation. Informally, Sabi ko nga, no? A permutation on a finite set X may be thought as an arrangement of elements on X in a row. Kasi, halimbawa, no? By the way, the way we would like to write permutations in math, no? Ayaw kasi natin Nagdrawing ng arrows all the time. Halimbawa, yung, eto yung x mo 1, 2, 3. Yung x mo 1, 2, 3 ang elements. If your permutation is pi, at ang pi ginagawa ito, for example, You don't want to draw these arrows all the time, diba?

**[45:37]** That's quite inconvenient. So what we would like to do is to write pi as follows. Ilalagay mo sa first position kung ano yung image nung 1 or kung saan dinala yung 1. Saan minap ba yung 1 dito? Minap siya sa 2. Saan ba minap si 2? Minap siya sa 3. So, lalagay mo yung 3 dito. Saan ba minap si 3? Minap siya sa 1. So, ang lalagay mo ay 1. Kaya yung arrows na ito, instead of drawing these arrows, diba, it would be convenient to just denote it as 2, 3, 1.

**[46:14]** Do you agree? And, at this point, dyan mo ma-realize bakit ang permutation ay tinatawag natin arrangement. Kasi it really disarranges the natural order 1, 2, 3. Kasi ang natural order natin yung 1, 2, 3, right? As it appears in the set X. But after applying the map... pi, or the mapping pi, yung 1, 2, 3 mo naging 2, 3, 1. So there's really an arrangement. So halimbawa, yung mga elements, for example, ng S sub 3, pag sinabing S sub 3, yung set natin ay may tatlong elements, 1, 2, at 3. So gagawa ka ng mga arrangements ng 1, 2, at 3. And in fact, there are how many? How many ways can you arrange 1, 2, and 3 in a row?

**[47:04]** Sige nga, sino makakasagot before I list them down? In how many ways can I arrange the elements 1, 2, and 3 in a row? Guys, sabi ni student 6. Okay, sabi ni student, 6. Sabi ni student, 6. Okay, pare-pareho kayong 6. How were you able to come up with 6? Can you share? kaano nyo nalaman yung six?

**[47:35]** Sabi ni student, three times, two times one. Very good. Sabi ni student, ayan, okay, alam nyo, no? You have an idea. Now, what are these six permutations? Thank you for your comments. The six permutations are listed Now, as follows, ayan yung 1, 2, 3, 2, 3, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 2, 1, 3. Because I have listed 6 already, sabihin, eto na lahat yun, wala nang iba. Okay? Paano po natin nasabing 6? 3 times 2 times 1. Ano yung ginawa natin ba 3 times 2 times 1? Kasi po, pag gagawa ka ng function from 1 to 3 to blank, blank, blank. Gagawa ka ng function, kanino ko i-assign si 1, si 2, si 3?

**[48:26]** Well, pag wala ka pang na-assign, There are three choices for one. Pwede mong i-assign si one, two, or three. Pero once that something has been assigned to one, dahil hindi pa pwedeng mag-ulit, one to one nga ka mo, dalawa na lang ang option para kay two. Di ba? And finally, kapag nakapag-assign ka na ng dalawa, I think... That third elementary has no option but to get to that whatever is left. Kaya it only has one choice already. By the fundamental counting principle, three times two times one is the total number of ways. Yan yung tinatawag natin Anong basa dyan? 3 factorial. Hindi yan yung 3 na nagulat, no? Hindi siya yung 3, yung galit na 3.

**[49:13]** Parang sunog, hindi ganun. Yung 3 niyan, ang basa dyan, 3 factorial. Yan yung meaning ng 3 factorial. I-multiply mo lahat ng integers from 3 down to 1. Okay? May binigay na formula si student. I think one is for yung set mo may n na laman, pero ang i-arrange mo lang are, kumbaga partial lang, partial permutation. Pero ang tinutukoy natin sa ating definition for now ay yung full permutation, lahat ng n, ginagamit natin, kaya n factorial. Kasi kapag ang n mo ay r, kapag ang r mo ay equal sa n, magiging 0 factorial yung denominator niyan, di ba? O, 1 lang naman yun.

**[50:03]** Okay, so, there is a way, there is a particular way, I want you to think of permutation in this way. Sabi ko, isipin nyo ang mga permutations ng S of N, they are actually manners of assignment. Nag-a-assign ka ng N applicants to N distinct jobs. Para kang merong Applicant 1, applicant, Jobs. Okay? Meron kang 1, 2, 3, 4, hanggang N na applicants. Meron kang 1, 2, 3, 4, N na jobs. Pag gumagawa ka ng permutations, right? Nagdadrawin ka ng arrows, diba? So halimbawa, this is one... permutation.

**[50:51]** It could be something like this. I don't know. This is an example of a permutation, right? Ang ibig sabihin na ito si applicant number 1 nailagay sa job number 3. Si applicant number 2 nai-assign sa job number 1. Si applicant 3 nai-assign sa job number 2. Did you understand why it can, it can be represented as a job assignment? Ang, ang restriction lang, dapat, each applicant, no? Distinct applicant, gets distinct job. Exhibit yan, walang, walang isang, walang dalawang applicant ang maglaland sa same job. Tapos after the assignment, walang jobs ang may iwanang unassigned.

**[51:38]** Did you understand? Yun, ganun yung gusto kong another way to think about it. So, kanimbawa, yung permutation na 312, I want you to think about this as pag sinabing 3, 1, 2, si 1 na-map sa 3, si 2 na-map sa 1, si 3 na-map sa 2 kasi yun yung order, no? 1, 2, 3. So 1 to 3, 2 to 1, 3 to 2. And yung ating classic way of writing this permutation is through arrows. It's represented on the right. And, you know, there are n factorial elements in S sub n kasi nga po, sa unang applicants, let's say, assuming walang qualification and all, it's just random assignment. So, pag walang qualifications, consideration at all, si applicant number 1, meron siyang N choices, N positions, right?

**[52:34]** Tapos si, pag na-assign mo si applicant 1, yung pangalawang applicant, N minus 1 na lang yung available kasi already filled in na yung isa. yung tindihan, and so on and so forth. Kaya, magkakaroon ka ng n factorial elements in S of N. Now, what I'd like you to tell about n factorial, it's very quick to rise in value. Meaning to say, 6 factorial, ilo na may 6 factorial? 720 na kagad yata yun. So, 7 factorial, 5,000 yata around. 8 factorial is around 40,000 already. So, mabilis siyang lumaki. It's even faster than exponentials. It's the idea.

**[53:21]** Now, you know, syempre, sa mga job assignments, um, kanito, sa mga job assignments, hindi laging may hustisya. Ang hustisya ay hindi laging nagwawagi, no? If we may say that. Kapag walang hustisya, ibig sabihin may inversion na nagganap. Ano bang ibig sabihin ng inversion? So let me tell you a story. Halimbawa, ito yung aking applicants, okay? Applicants, jobs. Now this time, yung numbers natin na 1, 2, 3, gagamitin natin yung pagiging integer nila. So, isabihin, bibigyan natin ng meaning yung magnitude. So, for example, 1, 2, 3 means si applicant number 3 yung pinaka mataas yung qualification. Maybe, for example, si applicant 3 may master's degree.

**[54:13]** Si 2 ay undergraduate. or graduate siya ng ano, ng bachelor's degree at C1 naman kunwari, undergrad. Maybe a high school graduate, right? Now this time, isipin nyo yung mga job numbers, yung weight o yung magnitude ng mga numbers na ito represent yung salary. Pag mas mataas yung job number, sabihin yan, mas mataas yung salary. You understand? Now, in an ideal world where justice prevails, ang natural way to map this or to assign is 1 to 1, 2 to 2, 3 to 3. Diba? Did you understand?

**[55:00]** Ito yung pinaka-ano, mayustation. Pero syempre, hindi naman laging nangyayari yan. For example, e pwede kang mangyari, although si applicant number one ay hindi nga nakatap ng college, pero nakapunta siya dun sa job that pays more. May pwedeng si ito, graduate siya, pero napunta siya sa job number 1, at si 3, napunta sa 3. So ang rightful, nasa rightful place lang dito ay si 3, si 1 at si 2 ay nagkapalit, no? ang tawag natin dyan, we call it an inversion. Ano ba ang inversion? Basically, an inversion is a pair of applicants, si R at S.

**[55:48]** Ang i-sabihin nito guys, si R ay isa dito, si S ay isa dito, no? Si R at S ay pair of applicants R is less than S. Ibig sabihin, ang qualification ni R ay mas mababa sa qualification ni S, pero ang sahod ni R ay mas malaki sa sahod ng S. Did you understand the definition? Kasi alam nyo, pag hindi ko kayo kakwentuhan ng ganito, Hindi nyo mahiintindihan yung definition eh, di ba? Pero kapag nilagyan natin ng ganitong kwento, mas madaling tanggap rin. Naintindihan ba yung definition as it says? O, di ba? Nag-make sense siya. So, tignan natin as an example yung permutation na ito.

**[56:35]** So, this time nasa S sub 5 value. So, may limang applicants, may limang job. Anong ibig sabihin ng notation na yan? Sabi ko sa inyo, notation lang yan. Ang ibig sabihin nyan, may limang applicants, limang jobs, So, si applicant number one nagpunta sa five. Oh, ang galing nito! Diyos ko! Anak siguro ng ano to? May ari ng kumpanya, no? Dahil tagapagmana siya kahit na hindi nag-aral yung hayop na yan, siyang may pinakamalaking sweldo. Ay! Mali pala ako! Sorry! Saan ba ako nakatingin? 1, 5, 3, 2, 4 pala. Okay lang pala. Diyos ko, pinintasan pa natin si 1, no?

**[57:20]** I mean, okay lang pala. Ito pala yung anak ng CEO, si 2, kasi si 2 yung nagpunta sa 5, may backer yan, no? Kasi 3, nasa rightful place niya. Si 4, magpupunta sa 2. At, sino pa? Si 5, si nagpunta sa 4. Sinong kawawa dyan? Ang kawawa dito si 4 at saka si 5. Do you agree? Ang kawawa dito si 4 at saka si 5. Kasi, yung nakuha nilang salary, position pays a little less corresponding to their qualification, no? So what are the inversions? What are the inversions? For example, the ordered pair 2-3 is an inversion.

**[58:10]** Iksabi nyan, si applicant, between applicant 2 at applicant 3 may nangyaring inversion. Bakit po natin nasabi? Kasi by definition, si 2 ay less than 3, pero ang pi of 2 ay saan nagpunta si 2? Sa 5. Saan nagpunta si 3? Sa 3. Mas malaki yung 5 kesa sa 3.

**[58:37]** Pero mas mahirap pang isulat ng ganito eh, diba? It's better to just look at these arrows, mas madali siyang maunawaan. Would you agree with me? Ano ko lang, i-copy at paste ko lang, ha? Kasi pag ililista natin ganito, medyo mas mahirap makita pa at mas mahirap intindihan, di ba? Ano pa yung mga May inversion, okay? Sige, pa-paste ko yung diagram dito. Alin dyan yung main, bakit si 2 at si 4 ay pair of inversion, pair consisting of inversion? Kasi nakita ninyo, si 2 nagpunta sa 5 pero si 4 nagpunta sa 2. In short, si 2, 5, no? Bakit si 2, 5 ay inversion? Kasi tignan niyo yung 2 at si 5, no? 2 plus 5. That's an inversion also.

**[59:25]** What else is an inversion? Si 3 comma 4 is an inversion. There you go. Kasi, 3, okay, rightful nga yan, pero yung 4, diba? That's also an inversion. So in short, how do we account for an inversion kapag nakita mo yung diagram, no? Kung titignan niyo yung definition, would you agree with me? An inversion happens every time that two arrows cross paths.

**[1:00:00]** Do you agree with me? Whenever we see the two arrows cross paths, that indicates an inversion. Tama ba si sir? Kalimbawa ito, isa, dalawa, tatlo, apat. Can you see those four crossings? These crossings correspond to the four different inversions. Okay? Ang tanong, bakit gusto natin malaman kung ano yung mga inversions. Actually, sa totoo lang, sa linear algebra, we do not care kung ano yung mga inversions talaga. What we care about is kung ilang inversions yung ginagawa ng isang permutation.

**[1:00:46]** So, sa case na ito, ilan? Atat. Wala nang iba, no? There are four, there are only four times where arrows cross. Where pairs of arrows cross. So there are four inversions. Ang magiging mahalaga lang sa lesson na to ay kung ilan. It doesn't really, ah, it's really immaterial kung Kung ano, kung ano-ano yung mga inversions, it will not matter. We don't care. What we care about is how frequent inversions happen. Okay? So ang tanong, kapag tititigan mo lang ito walang arrow, mas mabisang paraan to check for the number of inversions, guys.

**[1:01:35]** Sige nga, can you give me, makakagawa ba kayo ng paraan to count the inversions without actually drawing the arrows? Kasi, you know, drawing arrows can be hard as well. Diba? Especially when the permutation is long, paano nyo malalaman? Any idea? Actually, this is what I do. Ano yung mabuti ha? Kasi ang natural order ay 1, 2, 3, 4, at 5. So, ibig sabihin, pag sinusunod mo yung natural... progression na ito, walang inversion, zero inversion, okay? So, in short, an inversion happens when...

**[1:02:21]** Ano nangyari? May tumag-quisit. Ah, do not disturb ako ah. Saglit lang. An inversion happens when... merong digit na mas malaki na nasa kaliwa, ng mas maliit. You understand? Halimbawa, sa kanan ng 1 meron bang mas maliit? Syempre wala. So starting from 1 walang inversion. Pero, tingnan nyo itong 5. Syempre, sya yung pinakamalaki. Pero, lahat nung nasa kanan niya, mas maliit. So, bawat isang yan, it accounts for an inversion. So, may tatlong inversion coming from 5.

**[1:03:08]** E sa 3, sa kanan niya, meron mang mas maliit, isa lang si 2. So, that's an inversion. Starting from 2, meron ba mas maliit sa kanan niya? Wala. So, ilang-ilang arrows yung naidrawing ko? Apat. Kaya apat yung inversions.

**[1:03:31]** Naintindihan? Sige, gagawin pa tayo ng isa. Halimbawa, yung permutation ko ay, let's say, 6.

**[1:03:42]** 614532. Okay, so let's count how many inversions does this permutation perform in S sub 6? Sa kanan ng 6, ilan ang mas maliit? Naku, ang dami. Sa 2, 3, 4, 5. Lima yan ka agad. Sa kanan ng 1, ilan ang mas maliit? Wala po. Sa kanan ng 4, ilan ang mas maliit? Isa, dalawa. Sa kanan ng 5, ilan ang mas maliit? Isa, dalawa. Sa kanan ng 3, ilan ang mas maliit? Isa lang. Tapos na. Ilan yung na-drawing natin? 1, 2, 3, 4, 5, 6, 7, 8, 9, 10. 10 ba?

**[1:04:30]** Tama ba si sir ng bilang? Okay, that's how you count the number of inversions quick. without actually drawing an arrow. Kaya ako lang naman pinakita yung arrows kasi I want you to understand what inversions do, na? Ano ba yan in real life? Kasi knowing the number of inversions a permutation performs allows us to classify permutations into even or add. Anong ibig sabihin ng even permutation? Pag sinabi kong ang permutation ay even guys, ibig sabihin it performs an even number of inversions. Kung add, eh di add. You understand? So for example, ito ba'y even or odd?

**[1:05:16]** Ha? Is this even or odd?

**[1:05:25]** What's the answer? Even or odd?

**[1:05:34]** Ilan nga yung permutation? Very good, student. Even. Okay, thank you for your responses. Even kasi po, there were four inversions and four is even. Okay, thank you. Ngayon. I will just list down or I will just run over a set of facts and you know, I can explain them to you. Kaya lang yung mga proofs for example will not be presented anymore kasi yung proofs na ito medyo mahahabang gawin and I don't want to spend time Justified. Maniwala kayo sa akin, teacher niyo ako. Sige sabihin, parang ganun, ginagamit ko yung authority ko as your teacher to make you believe na ito'y totoo, okay? Ang reason, we don't have the luxury of time.

**[1:06:24]** Alam nyo naman, medyo nagkahabol tayo, diba? Okay. Una sa lahat. meron tayong kanatawag na identity permutation. Yung identity permutation, siya yung permutation na may justi siya. In short, siya yung permutation na 1, 2, 3, 4, hanggang N. At yung notation natin para sa kanya, ID sub N, i-sabihin yan. 1 to 1, 2 to 2, 3 to 3, 4 to 4, 5 to 5. They understand? Meron bang inversion na pineperform ang identity? Wala po kasi eh. May hostesya nga eh, no? Justice prevails. So walang inversion na nagaganap, so ano ba yung zero? Is that even or odd? So, it is considered even.

**[1:07:14]** Agree?

**[1:07:19]** Do you understand? Okay. Sa totoo lang, kapag dilista mo lahat ng mga permutation sa S sub n guys, kalahati dun ay even at kalahati dun ay add. Nice na. So in short, ano? Pantay. In short, kalahati ay even, kalahati ay odd. So tingnan natin, for example, yung S sub 3, guys.

**[1:07:47]** Ito yung S sub 3, ito yung E identity, pwedeng ang gawin ko, 2, 3, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1. 2, 1, 3. Okay. Let's look at this permutation. Sino dito ang even at add? So maybe you can count. This is even kasi walang, walang ano, walang inversion, right? Ito ilang inversions ang ginagawa? Isa, dalawa. Tama ba si sir? Dalawa. Dalawa nga ba yun? Yes po, even po yan. Eh yung 3, 1, 2. Isa, dalawa. Uy, dalawa lang din. So this is again, even. Eh eto, isa. Oh, isa lang. So add yun. Eh yung 3, 2, 1.

**[1:08:41]** Isa, dalawa, tatlo. Ano ba yung 3? Odd. Ayun, 2, 1, 3. Isa. Oo, isa lang. So, odd. Nakita nyo ba? Tatlo dun sa anim ay even, tatlo dun sa anim ay odd. Magkasingdami sila. Agree? Kalahati ay even, kalahati ay odd. So this property is hard to prove, so we will skip it, but nevertheless it's true, it can be proven. Pangalawa, this is an interesting property guys. Sabi dito, If two places of two elements in an even permutation are switched, pinagpalit mo yung dalawang numbers dun sa permutation mo.

**[1:09:34]** Yung resulting permutation daw becomes odd. Kung odd ka naman ang galing, nag-switch ka ulit, magiging even naman.

**[1:09:45]** Did you understand? Alimbawa, yung 1, 5, 3, 4, 2. Okay. Tingnan mo natin kung ito ay even or add. Isa, dalawa, tatlo, kapat. So this is even. O, sige. Sinong gusto nyong pagpalitin natin? Let's interchange, for example, 5 and 4. So, mangyari, 1, 4, 3, 5, 2. Did you see that I interchanged 5 and 4? Okay, so that's what I did, okay? Bilangin natin ulit yung inversions now. Isa, dalawa, tatlo.

**[1:10:31]** tapat, parang mali, isa,

**[1:10:41]** ulit nga,

**[1:10:46]** bakit, even pa rin, wait,

**[1:10:52]** oh, meron akong hindi nabilang dito, oh, Bobo Scissor, yung una pala ang mali, ito, I did not count that,

**[1:11:04]** nakita nyo ba? Hindi ko nabilang yun, so, 3, plus 1, 4, 5. Ah, add pala ito. Nung pinagpalit natin si 4 at si 5, ito'y nangyari, sa 2, 3, 4, naging even na nga, okay? Masubukan natin pagpalitin ulit si, let's say, si 2 at si 3.

**[1:11:33]** Okay, bilangin natin ngayon yung inversions. Isa, dalawa, tatlo. Add ulit siya. Naintindihan niyo yung property number three? The parity parity kasi ang tawag sa evenness or addness, okay? Parity. The parity of the permutation changes or switches from add to even, even to add whenever you switch two elements in a permutation. This is a very important fact, ha? So, you have to remember this. Then, I move on to the next slide.

**[1:12:16]** So, alam na natin kailan even or add, right? Meron akong notation na gagamitin in the definition of determinant. So, I will have to tell you about it. So, pag meron akong permutation na pi, At nakakita kayo ng expression na negative 1 raised to pi. Sinulat ko sa blackboard, negative 1 raised to a permutation pi. Dalawa lang ang meaning niyan. Ang meaning niyan is either 1 or negative 1. It is going to be 1 kung even si pi Kung si pi naman ay odd permutation, it's going to turn out to be negative 1. Yung notation na ito was inspired by the fact na ang negative 1 pag niraze mo sa even na exponent, 1. Agree? Yung negative 1 pag niraze mo kasi sa odd na exponent, it's negative 1.

**[1:13:08]** So, doon na-inspire yung notation na ito. But, nevertheless, this is just a notation that I'd like you to follow. And finally, we can now be able to define the determinant of an n by n matrix. Ito na siya, nakakatakot. Oh my God, di ba? titigan nyo yung definition, it's kind of scary. So nakakakita kayo ng summation and et cetera, oh my good lord, what does this mean? So alam nyo, wala naman talagang hindi mapapag-usapan at mapapagpaliwanagan, no? So let me share. what I think about the definition and how I want you to think about this, no? Ganito yan.

**[1:13:54]** Ang determinant ng isang n by n na matrix, guys, ay isang scalar. Yun yung una sa lahat, no? Scalar ang determinant. So in short, isang number siya. Okay? How do we compute this number from a matrix? Kung baga yung matrix mo, nagiging isang scalar na lang. Nag-associate ka na isang number to a square matrix A. So how? The determinant, as you can tell, it's a summation. So it's a sum. Dahil nakikita nyo yung factor na ito, remember ito parang switch, positive 1 or negative 1. So in short, ito yung nagsasabi kung yung term mo ay positive or negative. It can be, the term is either positive or negative. Now how many terms does this sum have?

**[1:14:39]** ang sagot, because the summation runs over all permutations in S sub n. Kung ilang permutation meron sa S sub n, ganun karaming terms meron yung sum na ito. Naalala nyo, n factorial lahat yun. Oh my god, good lord, no? So kung ang matrix nyo 10 by 10, ilang terms meron yung determinant? 10 factorial. Oh no! Kaya alam nyo, bigyan ko kayo ng 10 by 10 determinant sa exam. Ewa ko kung di kayo himatayin.

**[1:15:15]** Magdala kayo ng electric fan sa exam, ha? Kasi, mainit yata. Imatayin na kayo sa init, hihimatayin pa kayo sa 10 by 10 na determinant. Baka yun lang ang gawin nyo hanggang sa dulo ng semester, no? In fact, even when you ask AI... Let's say, ask nyo si Gemini, ask nyo, magbigay ako ng 10x10 na determinant, no? I-ask nyo yung Gemini, maghahang siya sa sabihin niya, ah, this is algebraically impossible, magdadahilan siya ng kung ano-ano. Kasi it's really a tedious work. Pero, Because we humans know theorems, know these properties and all, makikita nyo hindi pala ganon ka ano.

**[1:16:02]** I mean, mahirak pa rin pero at least may paraan. Makikita ninyo. Instead of going over the 10 factorial terms. Ano bang itsura ng bawat term? Mapapansin nyo dito, ito yung mga entries nung matrix, right? Kasi A yung matrix eh, no? Tignan nyo yung subscript nung mga or indices nung mga entries na ito. Yung row numbers, pataas ng pataas, 1, 2 hanggang n. So in short, kumukuha ka ng entry coming from row 1, row 2, row n, minumultiply. Tapos ang sign ay depende kung anong permutation ang pipiliin mo. yung permutation, ginagamit mo siya dun sa column number.

**[1:16:51]** Okay, ulit. Sa bawat row, starting from row 1 hanggang row n, kumukuha ka ng tigitigis ang element. Ang tanong, saan sa row 1? Saan sa row 2? Depende siya kung anong napili mong permutation. Ang idea, dahil ito ay permutation, kumukuha ka ng tigi-tigi siya sa bawat row nang hindi ka umuulit ng columns.

**[1:17:18]** Naintindihan niyo yan? Lahat ng mga combination ng rows at columns na hindi umuulit ng rows at columns. Pag minultiply mo, Isa yun sa terms nung determinant. Tapos i-determine mo pa kung positive or negative kasi depende siya kung yung permutation na pinili mo ay even or odd, okay? Okay, mag-alala, I have a lot of examples to illustrate what this definition means. Ang importante, Alam nyo that the summation is taken over all the permutations in S of N, just like what I've said, kung ilang permutations meron si S of N, ganong karaming terms meron yung determinant. Pangala, ayan na nga, no? And, In summary, every term of the determinant of A is a signed product of n entries obtained by taking one entry from each row such that no two entries are in the same column.

**[1:18:20]** Do you understand that? So, imaginein mo parang may aisle yung grocery, no? O, let's say may apat na aisle yung grocery, tapos may apat din na columns, for example. The idea is, what's the idea? O, yan yung, kukuha ka ng tigitigisa from each row, yun ba, kuha ka sa row 1, na nasa column 2. Pag kumuha ka sa row 1 at column 2, bawal ka nang kumuha ulit sa row 1 at column 2. Ang choices mo na lang sa susunod na row ay column 1, 3, they understand?

**[1:19:01]** Ay, up 5 pala to. Bobo. Paintindihan? Option mo na lang sa second row ay column 1, 3 at 4. So pag pinili mo ito, Let's say, bawal ka ng, band ka na ngayon pumili dito, dito, dito. Sa third row, ang pwede na lang, dalawa. So, kapag ito pinili mo, mababan ka na from, walaan ko ng blue ha, band ka na from using this. Ito, ban ka na from using this. And therefore, makikita nyo sa last row, ang tanging option mo na lang ay ito. So, ang gagawin mo dyan sa mga entries na yan, imultiply mo sila at isayod sa mga terms ng determinant. Ngayon, kung positive or negative yan, depende kung anong permutation yung napili mo. Dito ba, palagay nyo ano yung permutation na nag-describe na itong choices na to? Dahil nauna kong pumili sa second column, po yun.

**[1:20:03]** Yung susunod pinili mo sa fourth column, for yung pangatlong nasa row 3, pinili mo sa first column, 1, at yung last element sa fourth row, pinili mo sa third column, that's 3. So that permutation corresponds to the permutation 2, 4, 1, 3. Ang tanong, even ba ito or add? You really have to know. Sir, parang sudoku po. Yes, somewhat. Correct. Isa, dalawa, tatlo, tatlo. Add ito. So yung product na itong mga to, pag multiply mo, lalagyan mo ng negative sign sa unahan. If you were able to generate all the combinations, tapos na yung determinant.

**[1:20:51]** It looks overwhelming, right? It is overwhelming. Huwag kayong mag-alala, hindi lang kayong na-overwhelm ako, ako rin, no? Kahit ngayon, no? In my level, no? Pag nakakita ko ng determinant problem, medyo bumibilis yung tibok ng puso ko kasi, you know, ibig sabihin nun, Ako. mag-multiply at mag-a-add ako ng maraming numbers na naman, nakakalito. Diba? Pero, just like before, may softwares naman that can calculate determinants. So, tignan muna natin syempre yung pinakasimples, pinakasimples, yung simplest case. yung simplest case ay pag 1 by 1 yung matrix. Syempre, pag 1 by 1 yung matrix, wala ka ng ibang choice.

**[1:21:38]** Yung determinant mo yung entry lang na nandun sa matrix. Wala na usapan na the complication starts whenever n is 2. Kasi kapag ang matrix mo ngayon ay 2 by 2 guys, ang titignan mong set ngayon ay si S sub 2. Si S sub 2 may dalawang permutations lamang, si 1, 2, tsaka si 2, 1. Alam nyo ibig sabihin ng blue, alam nyo ibig sabihin ng red, kaya ako kinulayan ng blue at red yan guys. Say na what it means. anyone, anybody could guess? Ba't kinulayan ko ng blue at red?

**[1:22:18]** Ha? Why do you think kinulayan ko ng blue at red yung 1, 2 at 2, 1? What is that for?

**[1:22:29]** Positive at negative. Yes, kasi these are the permutations that are even and odd. Yung blue, even yan, kasi wala siyang inversion. Si 2-1 may isa, so that's the odd one. Tandaan nyo, kalahati ay even, kalahati ay odd, kaya ang determinant mo, kalahati ng mga terms ay positive, kalahati ng mga terms ay negative. Does that make sense? Anong gagawin natin sa mga permutation na ito? Yung unang term nyo, tandaan nyo yung row number laging nag-i-increase. 1, 2, 3, hanggang N. Yung pangalawang, yung column numbers, kukunin nyo dun sa permutation. Halimbawa ito, 1, 2, diba? Nalagyan nyo dito, 1, 2.

**[1:23:17]** That's the blue one. Positive yan. Eh ano yung second term? Yung second term mo negative, kasi red po siya. Yung 2, 1, dalagay mo dito, 2, 1.

**[1:23:32]** Naintindihan? It looks very hard, but in reality, pag 2 by 2, ang ating mnemonics ay ganito, no? Ito lang kailangan nyong tandaan. Yung blue term mo is this arrow down, okay? Yung red term mo is this arrow up. Did you notice, i-multiply, pa-ba-ba, multiply pa taas, yung diagonal, yan yung dalawang. Terms ng determinant. Make sense?

**[1:24:10]** Ay, ang tindihan ba? Ay, anong nangyari?

**[1:24:19]** Ang ginawa ko. Okay. So halimbawa, kapag 2 by 2, kapag 2 by 2, ano itsura? Pag ang determinant mo ay yun, By the way, pag determinant pala, ang ginagamit nating notation ay imbis na square brackets yung delimiter nung matrix natin, pinapalitan natin ng parang vertical line lang to indicate that we're evaluating a determinant. Okay? So, in this case, this is 2 times 4, tapos yung pangalawang term yung negative 3 times 1. So, subtract mo nga lang yung negative 3 times 1 kasi paakyat sya. So, you don't have to memorize this sa totoo lang.

**[1:25:05]** Tandaan nyo pag 2 by 2, ganun lang yung determinant. Any other 2 by 2 matrix, marunong na tayo ngayon mag-determinant. Okay ba? Pusin yung mag-move sa 3 by 3? Okay, papakita ko sa inyo yung 3 by 3 na ngayon. Ito na, 3 by 3 na tayo. Ano nang set ang titignan natin ngayon? We now have to look at S sub 3. Ilan nga yung laman ng S sub 3? 6. Ito yung nilista ko kanina. But this time, kinulayan ko yung mga elements so that you can see the even ones and red as the odd ones. Inidentify naman natin ito kanina, no?

**[1:25:50]** So, the blue terms correspond to the positive terms, the red terms correspond to the negative terms. And if you list them down, the positive terms first, makikita ninyo yung row numbers are fixed, 1, 2, 3, 1, 2, 3, 1, 2, 3. Yung column numbers adapt the permutation. So for example, itong 1, 2, 3, ito siya. 2, 3, 1, ito siya. yung 312, eto po siya. Make sense? At yung mga red terms naman, eto sila. Lahat sila, ah, bawat isa sa kanila was preceded by a minus sign kasi each one corresponds to an odd permutation. May making sense? Now, do I have to memorize this?

**[1:26:39]** Fortunately, no. Meron tayong mnemonics for the 3x3 case. So let me show you the mnemonics. Nasa kaliwa yung determinant at nasa kanan naman yung original na matrix, okay? What you can do to remember this formula, I want you to i-imagine ka na i-extend mo yung matrix mo sa kanan. Uulitin mo yung first column tsaka second column. Did you notice? Inulit ko lang. Nagwa ka lang ng redundant columns. Uulitin mo lang yung first column at second column. Tapos, anong gagawin? yung mga blue terms, guys, are the three down arrows. Umultiply mo lang yan. Did you notice?

**[1:27:24]** Sila yan?

**[1:27:28]** Nanotice nyo ba? Okay? Now what are the red terms? The red terms are the three upward arrows as it turns out.

**[1:27:42]** Okay? So, mahirap ba siyang gawin? Hindi naman. Mukhang, I mean, reasonable naman. Okay? So, let's try to practice. Halimbawa, ang determinant natin ay ito. So, how do we evaluate such a determinant? Well, One way to do this is to extend this, reimagining the first row and the second row over here. Now remember, these are not really here. Nilalagay lang natin sila dyan for the sake of evaluating the determinant but it's not really there. Talagang 3 by 3 lang yung determinant, okay? Okay, malilito ha? So kunin natin yung tatlong down arrows, tsaka yung tatlong up arrows. Siguro, ganito na lang.

**[1:28:36]** Para hindi, hindi natin mababoy. Entendyan nyo ang aking ginagawa? Ha? Okay, para hindi matabunan yung mga numbers. ang isabi nun, i-multiply lang natin sila. Parimbawa, 2 times 2 times 4, anong 2 times 2 times 4? Ayan na, ayoko na. Ano ba yun? 16. Next, negative 3 times negative 1 times 3. positive 9. Next, 5 times 1 times negative 1, negative 5. Ang ginagawa ko, ang aking practice, nilalagyan ko ng isang minus sign lang, tapos parenthesis, para nakagrupo lahat ng mga negative na terms.

**[1:29:29]** Para, I mean, hindi ka mag... Ewan ko, I feel like... Mas maliit yung chances na magkamali ako pag nakagrupo lahat ng mga negative. What do you think? Style nyo yan. Sa limbawa, yung pa-upward na tayo, 3 times 2 times 5, 30 yun. Negative 1 times negative 1 times 2, positive 2. 4 times 1 times negative 3, that's negative 12. Naintindihan ninyo? Did you understand the method? Sige, let's finally do the computation. This is 20 minus, what the hell? 32 minus 12 is 20.

**[1:30:23]** Tingnan nyo, ang haba-haba nang ginawa natin, ang sagot ay zero. Walang yang yan. Ang favorite ng mga math teacher yan eh, no? Ang haba-haba nang ginawa mo, tapos, shit na yan, ang sagot lang pala ay zero. Okay. Python code. Okay. numpy code. Kung kayo'y gagamit ng numpy to evaluate the term, di ba? You are defining a matrix using the np array function. Do you remember this? Di ba? 2 by 2. 1, 2, 3, 4. Can you imagine the matrix A? A po natin ay 1, 2, 3, 4. Sa numpy, to evaluate the determinant, you just print np.

**[1:31:21]** Okay, gagamit ka ng anong nga pala dito ng linalg na sub. library, if you remember it, tapos .det, tapos lagay nyo A, okay? So, if you execute this line of code, ipipring nyo yung determinant nung matrix A, which is 4 minus 6 negative 2, okay? Kung available naman yung calculator ko sa inyo, no? Halimbawa, ito siya. Ito yung ginawa natin last time. May function dito na, yun o, number two, function number two, depth. Marunong nga rin siya mag-inverse eh, yun yung number three. Can you see that? Nababasa niya ba yung mga functions?

**[1:32:10]** So, naintindihan na natin ngayon yung determinant, inverse, matrix rank. Yung matrix rank, kung ilan lang yung pivot in the RREF. Transpose, alam na natin yun. Identity matrix, alam na natin. Row reduce, alam na rin natin. Di ba? Unti-unti na natin natututuhan ito, no? At the end of the semester, we wish to... know all of these functions. But, for this lesson, we would like the determinant. Tapos, ano yun? Ah, yung button. Anyway, alpha matrix. Three, ah, let's say three by three. I-check natin tong example natin. Kung 0 nga ba talaga,

**[1:32:56]** ulit, negative 3, 5, second row is 1, 2, negative 1, so 3, negative 1, and then 4. You see? Anong nag-appear na determinant? It was really 0. And, uh, we believe we are right.

**[1:33:21]** Pero alam nyo guys, bago pa, bago pa, ko pa man gawin ito, alam ko na na ang sagot ay zero. Siyempre, maliban sa ako yung gumawa, pero meron kasi akong na-observe sa kanya. I don't know kung na-observe nyo rin ba? Tulad ko yung matrix A na original dito.

**[1:33:43]** wala kayong napapansin na anything weird?

**[1:33:50]** Wala. Hindi kayo as observant, no? Wala kayong napapansin? Ito. Pansinin nyo ito. Itong row number 3. Kung mapapansin nyo, si row number 3. ay resulta pag in-add ko si row number 1, at si row number 2. Did you notice that? Pag in-add nyo yung row 1 at row 2, 2 plus 1, 3. Negative 3 plus 2, negative 1. Oh my god! 5, negative 1, 4. Ah, okay. In other words, row 3, is actually redundant. In fact, yung column 3 din, yung column 3, so subtract mo naman column 1 minus column 2. Subtract nyo, column 1 minus column 2.

**[1:34:41]** Check nyo, column 3 yung lalabas. So in other words, there are redundant information in your matrix. Kasi alam nyo yung determinant, alam nyo kung ano pang chinecheck nya? Chinecheck nya, pag ang determinant ng square matrix nag 0 guys, ibig sabihin there are redundant columns and redundant rows. There is at least one. It's an indication that there are redundancies in the memory, so you may want to delete them. Siyempre, sayang naman yung ano, kumbaga, ang ibig sabihin ko ng redundant, combination lang siya nung other vectors in your set. Kumbaga, itong row 3, hindi mo naman talaga kailangan ito, kasi combination lang siya, makukuha mo siya, makukuha mo yung information na to from rows 1 and 2.

**[1:35:32]** So, it doesn't really have to be in the memory, right? Naintindihan ninyo? Kasi, sa mga susunod na lesson, pag-uusapan natin yung paano ba maglinis ng data, no? For example, how do you clean out the data? Paano ma-spot kung may redundancies? Determinant can be a good tool but, you know, there are other tools later. For now, focus muna tayo sa determinant, okay? Before I proceed guys... I'd like to tell you, na although yung mnemonics ko for 3x3 ay fascinating and, you know, very convenient kasi madaling tandaan, you don't have to memorize.

**[1:36:18]** I am very sad to tell you na yung method na yun ay hanggang 3x3 lamang. hindi nyo pwedeng gawin yan sa 4x4, 5x5, 6x6. Bakit? So let me share why. Halimbawa kapag 4x4 na, let's say, ito yung matrix nyo, 4x4. Huwag na natin lagyan ng entries. Lagyan ko ng tuldok so you can see, no?

**[1:36:47]** Bakit hindi nagana yung down, down, down, down, up, up, up method? Kasi kapag 4x4, tingnan nyo yung mga down terms. Ang mga down terms, isa, dalawa, tatlo, apat. Okay? Ang mga up terms, isa, dalawa, tatlo, 4, 10. So ilang terms lang ang ma-digenerate mo lahat? Ang ma-digenerate mo lang ay 8 terms. You're missing out 16 terms. Pag ginawa mo kasi yung 6 na yun, ang ma-digenerate mo lang na terms ay 8, whereas, ilang terms ba meron ng determinant? 4 factorial or 24, 16 terms yung nawala.

**[1:37:37]** You did not account for these 16 combinations. Halimbawa, nasa na yung mga 16 terms na yun. For example, ito, itong combination na to, this was really not part of any of these arrows. Did you notice? May mga weird combinations kasi habang lumalaki yung matrix na hindi nasasakop ng mga down arrows at up arrows na yan. Nagkataon lang nakapag 3 by 3 kasi, 6 yung na-generate mo, kaya tapos na. Pag 4 by 4, 8 lang yung mag-degenerate mo whereas there are 16 other terms. Naintindihan nyo si sir? Ano

**[1:38:25]** lang gagawin natin kapag mas malaki na sa 3 by 3? Yun yung pag-uusapan natin in the next few slides. Okay? But for now... Matandaan nyo yung sinabi ka ha, warning po. Kasi alam nyo, lalo yung mga student pag nag-e-exam, pag-desperado na sila, hindi nila matandaan kung paano kunin yung 4x4 na determinant. Ang ginagawa, nagga ganun lang, down-down, kalan lang bibigyan ko ng points. No. alam kong sinadya nyo yan soliciting 4 points, pero you did not really know. Diba? Kasalanang mortal kasi sa linear algebra yan na gamitin yung 3x3 na method sa 4x4 because it's not really applicable. But this time, try natin itong 5x5.

**[1:39:13]** Use the definition Ibig sabihin ba kailangan mong gawin yung 120 or 5 factorial na terms? All in all, hindi naman. Kasi, you know guys, may mapapansin kayo sa matrix na to. Ano na pansin natin? Maraming zeros. Diba? Once na mahugot mo yung zero, Dahil minumultiply natin to get the term of the determinant, automatic zero na kagad yung term. So in short, to have a non-zero term, pumili ka ng hindi zero. So for example, comment, almost all terms.

**[1:39:58]** are zeros. Actually, except for one. Isa lang ang term na hindi zero. Ano ka makakakuha ng non-zero term? Siyempre, dapat sa first row wala kang ibang option but to select the one. They agree? Siyempre, pag kinuma mo yung any other in the first row. Diba? Sabi ba si sir? O sa second row, sinong pipiliin ko? Wala naman ako ibang option. Si Tulak. Diba? E sa third row, wala rin akong ibang option. May violation ba ako? Wala naman, hindi pa ako nagre-repeat ng column. Sa fourth row, si four lang. Sa 5th row, can I select any?

**[1:40:46]** Can I select 5? No. Kasi kapag piniti mo yung 5, aawayin mo yung 3 sa taas. Kapag piniti ko yung 6, aawayin mo yung 1 sa itaas. Kapag pinili mo naman yung 8, aawayin mo yung 4, yung 9, aawayin mo yung 2. ang papwede mo lang piliin talaga ay yung 7. And you do not really have a choice. Kaya nga sabi ko dyan, as the comment says, almost all terms are zeros except for one. In fact, yung lone term, lone non-zero term, may iwan ay 1 times 2 times 3 times 4 times 7. Pero, you further need to determine kung ito ba ay positive or negative.

**[1:41:33]** Paano mo malalaman? Alamin mo kung ano ba yung permutation pi corresponding to that combination. So, to do that, you take note of the column numbers, okay? Halimbawa, column number neto? Two. Column number neto? Five. Column number neto? One. Anong column number neto? Four. And of course, finally, ito ay column number 3. So, the permutation used to generate this term is the permutation 2, 5, 1, 4, 3 which is even or odd? Isa, dalawa, tatlo, apat, lima, anin ba?

**[1:42:23]** Ay, hindi, nagkuha na pala yun.

**[1:42:29]** Tama ba? Naguluhan ako? Shit. Ulit.

**[1:42:35]** Isa, dalawa, tatlo, apat, lima lang, no?

**[1:42:47]** Am I correct? So therefore, the determinant is really negative. Ano yung 28 times 7? O, tsang to. Ayok. 128 times 7, 86.

**[1:43:05]** Tama ba si sir?

**[1:43:09]** Negative 196. Was I correct? Yan. So yung the determinant is negative 196.

**[1:43:22]** Get? Intyende?

**[1:43:27]** Medyo natakot lang tayo kasi nakakita tayo ng 5x5. Akala natin gagawin natin lahat ng 120, no? No. Kasi napansin nyo marami namang zeros. Make sense? Make sense ba example na ito? Okay, before I continue... Ano bang kinocompute ng determinant? Okay, ito'y wala kasi dito sa slide ko, but nandun sa lecture notes, hindi ko pa yata na-upload to, sorry, yung portion ng determinant. Kaya lang, okay, kapag binasa nyo itong notes, makikita nyo some of the notations are different, kasi nga I've written these notes. a long time. Matagal na ito, hindi ito updated, so you may find some other notations na iba sa slides na ginagamit it ko, nevertheless parehas lang ng meaning.

**[1:44:24]** Okay, can you see the notes? You can just zoom it in, ha? Ito yung notes na i-upload ko. Pa yata na-upload tong lesson na ito or na-upload ko na. I don't know. So there you go. I mean, you can read it. Ayan. Ito yung portion that I'd like you to know. Ano bang kinakalculate ng determinant? Actually, ah, hindi pa na-upload. Okay. I will upload it later this day. Okay. So, um, ano bang kinakalculate ng determinant? Well, ito yung main idea dyan. Yung theorem number. 16. If M is a 2 by 2 matrix, indeterminant of M with an absolute value, so iksibing the determinant can be negative kasi, diba?

**[1:45:16]** So when you disregard the negative sign, it represents the area of the parallelogram in R2 determined by the column vectors of M, what does that mean? So let me, oh my god, wait a minute, para makita nyo ng buo yung aking screen and everything i-re-share ko. Mali ako nang na-i-share. Share ko na lang yung aking entire desktop,

**[1:45:48]** okay? Can you see my slide along with the notes?

**[1:45:58]** So, there you go. Punta tayo sa scratch. Ang sinasabing yan, let's say si A, I2 by 2. A, B, C, D. Okay. You know, when you look at the columns, meron kang dalawang columns, diba? A, B. tsaka si CD. When you sketch them in the Cartesian plane, kunwari eto si AB,

**[1:46:32]** eto naman si CD kunwari, let's say, pag daw kinuha mo yung parallelogram, defined by this vector. So nasa na yung parallelogram na yun? Di ba ito yung parallelogram na yun? Kama ba si sir? And when you try to look for the area of this parallelogram, ito yung area ng parallelogram, guys, yung area na to, Regardless of, I mean, if you disregard the sign, ito yung, sorry, ito yung absolute value ng determinant ni A. Kapag kinumpetween determinant ng A, it has to be the area.

**[1:47:23]** Okay, bakit siya naging area? Medyo mahaba yung computation, but it is available in the notes. Ito yung notes ninyo. Okay? So let me find that derivation for you. Medyo mahaba. Nagsimula ako sa triangle. Okay? Nakita nyo o. kumamit ako ng mga area ng trapezoid, etc., so to illustrate the fact. Nagsimula ako sa triangle, tapos from there, ginawa ko yung parallelogram na ito, kasi ang parallelogram, dalawang triangle lang naman, diba? Napuputulin mo, times two. sa times 2 mo lang yung makukuha mo sa taas. Tapos, as it turns out, yung determinant na yun is just this.

**[1:48:12]** And then, furthermore, alam nyo guys, pag 3 by 3 yung determinant naman this time, pag 3 by 3 naman yung A, let's say ito yung A, no? Kasi si AI 3x3. Siyempre, ang scalars dapat real numbers, okay? Meron siyang tatlong columns, right? At yung mga columns nyan ay nasa R3 na. When you say nasa R3, nasa 3D space na. Did you understand? Ano ba itsura ng 3D space? Ako rin, ito yung x-axis. Ito yung y-axis nasa kabilang side, at ito yung z-axis. Okay? Kunwari yung tatlong column, columns ng AI ito. Ito yung isa, ito yung pangalawa, ito yung pangatlo, okay?

**[1:49:04]** Now yung tatlong vectors na yan do not really form a parallelogram. Bawat pair, ay nagpo-form ng parallelogram, tama kayo. So ito yung parallelogram ng dalawa, ito yung parallelogram na itong pair na ito. Can you imagine that? At yung parallelogram ng dalawa ay, okay? As you can see, yung tatlong parallelograms na yan, they actually define a solid.

**[1:49:32]** Can you imagine the solid, guys?

**[1:49:38]** Ang tawag dito, guys, ay parallelepiped.

**[1:49:48]** Okay. It's a parallelepiped. Hindi ko alam kung ito ba ay E or I. Nakalimutan kong paralelepiped or parallely. Can you just check it later, but... the name is parang ganyan, parallelepiped or parallelepiped. I forgot the correct spelling but definitely that's it. Yung determinant ng A, as it turns out, ignoring the negative sign will measure the volume of this parallelepiped. It is going to be the volume. Kaya nga ang n by n determinant, guys, sa totoo lang, pag ito'y n by n, this is an n-dimensional volume.

**[1:50:39]** Hindi natin nakikita ito, pero, yeah. I have to write signed volume, kasi pag yung determinant, kasi, pwedeng negative, diba?

**[1:50:54]** Is the n-dimensional signed volume of the n-dimensional parallelepiped

**[1:51:05]** defined by the columns of A.

**[1:51:13]** Naintindihan nyo how it extends? the n-dimensional case. Pero, of course, wala na tayong drawing para doon. Ang kaya lang natin i-drawing ay hanggang 3x3. Naintindihan ninyo? So basically, the determinant measures a mass of objects na dinidefine ng mga columns na Okay, punta na tayo or mag-focus na tayo dun sa ating scratch board. Nabanggit ko lang what it geometrically represents. Should you be curious to read about but nandun sa notes natin, okay?

**[1:51:52]** Okay, hopefully I am back sa aking blackboard.

**[1:52:01]** Alright, let's talk about this. Let's look at an upper triangular matrix first. Pag sinabing upper triangular, do you remember yung mga entries sa ilalim ng main diagonal are all zeros? Hindi ko na sinulat yung mga zeros but ang ibig sabihin ko ng mga blank dyan, ibig sabihin yan yung mga n elements na yan are just all zeros, okay? What do you think is the determinant of A kapag siya ay upper triangular, guys? Anyone?

**[1:52:36]** Kasi maraming zero eh, no? Kagaya nung ating na-point out kanina, almost maraming zeros. Halimbawa, pag nagsimula ka dito sa second element na ito, Definitely kukuha at kukuha ka na ng isang zero dito sa column na ito. Do you agree? Kung dito ka naman magsisimula, makakakuha at makakakuha ka ng zero somewhere in the middle, diba? The only way you can avoid the zeros is to just use the main diagonal. Do you agree? The only way you can avoid zeros is to select the main diagonal. And in fact, if you look at the permutation used by the main diagonal, it's basically the identity permutation, which is even by default.

**[1:53:27]** Kaya nga alam ninyo, pag upper triangular ang matrix, the determinant is simply the product of the main diagonal regardless of the size. Tandaan niya yan ha? Pag upper triangular ang matrix, ano? Pag upper triangular po, ano masasabihin ko? Regardless of the size, the determinant is just the product of the main diagonal entries. And in fact, hindi naman iba yung sa lower triangular. Ganon din, pag lower triangular, ang determinant mo, then ay simply the product of the main diagonal entries.

**[1:54:13]** Kaya magka-follow guys, lalo na kapag ang matrix ay diagonal. Kapag diagonal, di mo multiply mo lang pala talaga yung main diagonal entries. Okay? So as an example, yung identity matrix, ang determinant niya ay 1. siyempre, di ba? Upper triangular siya, lower triangular din naman siya, kaya nga siya diagonal eh, di ba? So, undetermined na identity matrix is just 1, kasi ang main diagonal entries niya are all 1, so kapag minultiply ko yun, 1. And obviously, ang determinant ng zero matrix ay zero. So diagonal din yan. And to be more general, once ng isang matrix ay may row o kaya column na all zeros, matik yan, ang determinant mo rin ay zero.

**[1:55:11]** Bakit? Kasi kukuha't kukuha ka sa lahat ng rows at sa lahat ng columns nang hindi nagre-repeat. Kaya once na meron kang row or column na maraming zeros, all zeros, lahat ng terms mo will have to be zero. Kasi makakakuha't makakakuha ka sa row or column na yun. Do you agree? Would you agree with me on that? Okay? Okay, tama. Alright, so at this point, we're now going to list down some properties of the determinant. Would you like to take a short break? Kuwa kayo ng pagkain hanggang 12.30 maybe. Sige, I'll give you some time, few minutes to get some food so you can eat while listening, okay? Hindi ko na ipopause yung recording kasi wala yatang pause.

**[1:56:05]** Just do it now. I'll be back maybe 3 minutes from now. 3 minutes lang, pasensya na kayo ha? Sige, kuha na kayong pagkain.

**[2:02:14]** Hello guys, I am back.

**[2:02:19]** Are you there? Are you listening?

**[2:02:24]** Let's continue para tayo itapos na, okay? Tapos. So, papunta na tayo sa exciting na park kasi we are now listing down. Uy, wala yung aking slide.

**[2:02:43]** saglit, ha? Ano nangyari? Let me check. Hmm, ayaw na naman mag-connect.

**[2:03:01]** Saglit lang. Share ko lang yung aking desktop. And then...

**[2:03:12]** Okay. So we are now down to the properties of the determinant. Can you see the board clearly, guys? Kasi... hindi ko mag, nawala na naman yung aking, yung app, nag-crash na naman yung ginagamit ko, so, ang ginagamit ko ngayon yung mismong ano lang ng Apple, yung native na Air, Airplay ba yung tawag dito. Kaya ng pag Airplay kasi, hindi ko nakikita yung UI nung MS Team, so, wait lang, kung meron kayong tanong, paki, ano ha, raise na. Okay, yung unang property that I'd like to talk about is about the transpose of a matrix. Ito nga nga yung sinasabi ko, no, minsan I'll be inconsistent with notations.

**[2:04:02]** Kasi ang gusto kong gamitin sana sa transpose yung capital T, pero pag nakakita kayo ng small t sa taas, I mean it also means sa transpose, ha? Ang reason kaya gusto ko ng capital T kasi sa Python ay capital T. Para lang pareha sana, kaya lang minsan na due to habits, na papag, ano ko, understand? Napapagpalit ko yung small t, tsaka yung capital t. So, I hope that you still understand, okay? Sabi nung property na ito, kapag daw, kinawa mo yung transpose nung matrix guys. hindi daw nagbabago yung determinant. And we know precisely the reason behind this. Kasi remember, per definition of determinant, kinukuha natin yung, kumukuha ka ng entry from each row without repeating a column.

**[2:04:55]** And when you do that guys, That's also precisely getting one from each column without repeating a row. They understand? Kaya lahat ng terms, nung determinant ng A, ay terms din nung determinant nung A transpose. Kasi sa transpose, Hindi mo naman binabago yung order eh. Ang nangyari lang, yung mga rows mo nagiging columns, yung mga columns mo nagiging rows. But precisely, yung mga entries mo are still intact. Kaya nga lahat ng term doon sa expansion ng determinant doon sa transpose ay actually terms din ng original na determinant. As a matter of illustration, let's look at these two determinants. Makikita ninyo, pareha silang 3x3 and one matrix is the transpose of the other.

**[2:05:44]** They agreed? They recognized, no? Na-transpose lang sila ng isa't isa. O, tignan nyo. Separately kunin nyo yung determinant. Halimbawa, yung una. Let's apply the down, down, down, up, up, up method. Without extending, kaya nyong imagine kung anong kasunod. Halimbawa, yung first down, that's 2 times 1 times 8, 16. Okay? Yung second down, pag-anon, dahil dito ka pupunta, ito yung kasunod. Okay? 3 times 3 times 2, 18. Third down, pa ganun yun. Kung i-imagine mo siya, i-re-re-imagine mo siya dito, ito yung kadugtong niya eh, no? It's really this, this and that.

**[2:06:30]** Do you agree? So negative 4 times negative 1 times negative 5. That's negative 20. O, yung mga up arrows natin. Kunin natin yung mga up arrows. Ito yung unang up arrows. First up arrow, that's negative 8. Second up arrow, pa ganon, kaya ito yung karugtong nun, di ba? Negative 5 times 3 times 2. I think that's negative 30. And, um, last up arrow, pag anon yun, so parang this, this, and that. Do you agree?

**[2:07:14]** Hopefully, you get the idea na, okay, first down arrow, second, third, okay? mga up arrows, eto, eto, and then, eto. Yes? Let's compute this. Ano ba ito? 34 minus 20, that's 14, minus 38 plus 24, ilan yun? 62, negative 62, so pag in-add ko ito, ano nga ba yan? Hirap ng MATH, Diyos ko day, 78 ba? 76?

**[2:08:02]** 76 no, sige. Tingnan natin yung determinant neto, dahil ito ay transpose lang naman, so dapat 76 pa rin. That's the idea. So, the first down, 16. The second down, 5 times 4, 20, pero negative tayo kasi tatlong negative yan. Third down, 18.

**[2:08:32]** Okay? First up, negative 8. Second up, negative 15 times 2, negative 30. Third up, 8 times negative 3, negative 20. Dito pa lang eh, di ba? Kahit hindi mo na actually ipagpatuloy, nakikita nyo naman yung mga terms are basically the same, right? Kaya kahit hindi mo na-competent, alam mong 76 lang din yung lalabas. Ang tindihan?

**[2:09:10]** Okay. It's the deal now with the transpose. Kaya ang reason kaya natin tinalakay na pareho lang ang determinant kung ni A saka nung transpose nya. Ang reason guys, kasi yung mga rows mo nagiging columns, yung mga columns nagiging rows when you do the transpose. Sa determinants kasi meron tayong tinatawag na duality property. When you say duality property, pag meron tayong isang theorem na na-establish about determinants and it talks about rows, no? Pwede nyo palitan yung salitang rows ng columns at theorem pa rin siya. Ibig sabihin, totoo pa rin kung papalitan mo yung salitang rows ng columns kasi interchangeable sila in terms of determinants.

**[2:09:56]** Naintindihan nyo? Bakit? Ang susunod kasi na gagawin natin tatalakayan natin yung effect o yung efekto sa determinant nung tatlong elementary row operations. So dahil elementary row operations ito, ang ginagalaw natin yung mga rows, diba? Ang sabi ng duality property, kung i-apply mo yung mga yun sa mga columns, totoo pa rin. yung results, okay? Tingnan nyo ito. Halimbawa, sabi dito, if a square matrix B is obtained from A by interchanging two distinct rows, anong ibig sabihin yan guys? Hmm? Ang ibig sabihin nun, nagpalit ako ng dalawang rows ng A to get matrix B.

**[2:10:43]** So, I applied a type 1 operation. According to the theorem, ang determinant ng B has an opposite sign. Ang magbabago lang sa determinant ng B ay sign. Sa determinant ng A ay yung sign. From negative magiging positive, from positive magiging negative. So, yung duality property kapag in-apply mo dito sa theorem na ito, what I'm trying to say is kung papalitan mo ito ng columns instead of rows, dotoo pa rin siya. So, kung mag-i-interchange ka ng dalawang columns, mag-change lang din yung sign ng determinant. Did you understand the duality property? How is it applied?

**[2:11:32]** Sige. Now, in symbols, pag ikaw ay nag-apply ng type row interchange sa A at naging B, or pwedeng column interchange, no? Pwedeng column interchange. Then, the determinant of B is just the negative of the determinant of A. Bakit po ganon? Kasi guys, do you remember doon sa ating determinant, pag nagpalit ka ng dalawang rows, yung mga permutations mo, nagpapalit lang din yung dalawang digits. Do you agree? When you interchange two distinct rows, yung mga permutations mo, yung dalawang digits sila nagpapalit lang din. And what do we know about interchanging digits in a permutation? From even nagiging add, from add nagiging even, so yung term mo kung positive magiging negative, yung mga negative terms mo magiging positive.

**[2:12:27]** Anong effect na sa buong determinant? Essentially, magpapalit lang yung sign ng determinant. Did I explain the reason? Naintindihan ba yung reason? I just explained the reason why nagpalit yung sign, ah? It uses the property na pag nagpalit, yan ang dalawang digits in a permutation, nagpapalit lang yung sign, yung evenness nung ano, nagiging odd, yung odd nagiging even. Yun precisely yung reason. Kaya ngayon, in other words, yung determinant nung Eij times A is just the negative of the determinant of A kasi ito yung elementary matrix corresponding to that operation. So as an example, halimbawa tignan nyo tong determinant na to. Minsan, pag ikaw ay nagmamadali, yung banat ka lang ng banat, gagawin mo na yung down, down, down, up, up, up method, na?

**[2:13:24]** Pero minsan, ma-observe mo, katulad na ito, may tatlong zero ako nakikita eh. Look at what I'm going to do, ha? Tingnan ninyo. What did I do here?

**[2:13:37]** What is your guess? Anong ginawa ko dito? As you can see... nag-apply ako ng E13. Pinagpalit ko yung dalawang rows nung matrix, row 1 and row 3. Did you recognize? Do you recognize that that's what I did? In effect, anong mangyayari sa determinant? magkakaroon ka ng negative 1 sa labas, okay? Now what do you think will I do next? Ang gagawin ko naman, pagpapalitin ko yung dalawang columns na to, because if I do that, magiging ganyan yung determinant. So ulit, yung unang step E13, ang pangalawang step, columns naman ang pinagpalit ko.

**[2:14:25]** Kapag columns ang pinagpapalit natin, guys, diba? Ganon pa rin yung notation, E1, 2, pero lalagyan ko ng C to indicate that I work on columns. Notation ko lang yan. Okay? Naintindihan? Ang igsabi ng C, yung columns ang ginalaw ko instead of rows. Pinagpalit ko yung column 1 at column 2. Tapos, may lumabas na additional na negative 1 kasi because each time na magpapalit ka ng dalawang rows or dalawang columns, nagtichange yung sign. In effect, anong nangyari dun sa determinant? Did you see na naging upper triangular ito?

**[2:15:12]** Diba? Eh, anong alam natin pag upper triangle? Ay, may numultiply lang yung main diagonal. So, the final determinant is simply just 9 times negative 1 times 2. So, you have prevented yourself from multiplying 6 times. Diba? That's how you use the type 1 operations. Usually, ginagamit ito pag mga ganyanong instances. Okay? Naintindihan ba? Sige. You know what other consequences this property has? Ito yun. Sabi dito, if a square matrix has two identical rows, pag meron talagang dalawang rows, or dalawang columns, for that matter, na identical, ang determinant daw automatic zero.

**[2:16:10]** Kaya nga, can you tell me why? Halimbawa, magbibigya ako sa inyo ng particular na example. Hindi ko kukumputein pero malalaman ninyo bakit ang determinant ay 0. Tingnan niya ha, magic to. Halimbawa na lang yung rows 1 and 2 ang pareho. Yan, ganyan. Kasi yung rows 1 at 2 ang pareho. Without computing the determinant, why do we think that the determinant is 0? So, here's the thing, guys. Kunwari, ang determinant ay D. Hindi natin alam, no? Yung D stands for, di natin alam. Charat. So, sige. Ang gagawin ni sir, pagpapalitin ko yung row 1 tsaka row 2. If I do that, Guys, may lalabas na negative 1, but you see, because identical lang naman yung row 1 at row 2 na pinagpalit mo, nagbago ba yung determinant? Hindi naman. This is basically negative D.

**[2:17:16]** So if D is negative D, That's 2D equals 0, that means D has to be 0. Gets? Can you see how this extends in general? Pag meron kang dalawang rows na identical, hawagin mo yung determinant niya na D. Pagpalitin mo yung dalawang rows na identical na yun, nagbago ba yung matrix? Yung determinant? Hindi. That's just D but now with a negative sign. So kung equal yung D sa negative D, magka-follow na ang D ay 0, kaya tatandaan nyo mula sa araw na to, pag nakakita kayo ng matrix no matter how big that is, Pag meron kang dalawang rows na identical, undetermined, automatic, zero.

**[2:18:06]** And you know guys, even when you have identical columns.

**[2:18:13]** Naintindihan? Even when you have identical columns. Gets? Hello? Tindihan nyo ha? Sige nga! Anong determinant na ito? Oh my god, 6x6 yan sir. What do you think is the determinant?

**[2:18:39]** What is the determinant?

**[2:18:44]** Can you tell me why? Yan, student, bakit 0?

**[2:18:53]** Okay. Nakakatawa yan kasi itong column na ito tsaka columns na ito, do you notice they are the same? Very good, student. So minsan kapag ano, pag... Pag, ah, what do you call this? Pag tinitigan mo yung matrix at nataranta ka, kukumpitin mo kagad, banat ka kasi ng banat, only to find out na may dalawang columns pala na pareho. May redundancy, no? So, automatic ang determinant ay zero. You don't really need to compute anything. Okay? Naintindihan ba? Oh. Okay. The terminal is really just zero. Alright. Let's now talk about the effect. Kapag naman, nagawa tayo ng type 2 operation.

**[2:19:41]** Ano nga yung type 2 operation? May isang row tayo na minumultiply by a scalar C. Ayan o. Sabi, if a square matrix B is obtained from a square matrix A by multiplying a row of A by a scalar, C. Ano raw ang relationship ng determinants nila? Yung determinant daw ng bagong matrix mo is just C times the determinant of A. So in short, ano? Pag nag-multiply ka ng isang row, isang buong row ha, isang buong row, yung original determinant mo, namumultiply din by C. Bakit po? Kasi, pag, let's say, A, B, C, D, E, F, G, H, I. Let's say, yung second row minultiply ko by K.

**[2:20:38]** Eh di ba? When you construct your determinant or when you complete your determinants, you're selecting one from each row and each column without repeating a row or without repeating a column. The idea is each time, kumukuha't kumukuha ka sa second row, wala kang choice, kukuha't kukuha ka dyan. So, therefore, because of that extra factor K, lahat ng term ng determinant mo ay may extra factor na K. So, pag lahat ng terms mo yung extra factor na K, you can factor it out. Pag finactor mo yun, ano? May iwanan yung original na determinant lang. Did you understand?

**[2:21:23]** Did you understand my explanation? Uh-oh. So in, in notations using elementary matrices, if you apply this elementary row operation on A, therefore multiplying it to an elementary matrix on the left. Yung determinant net is just C times the determinant of A. And as a consequence, pag yung buong matrix ang minultiply nyo by a scalar C, yung buong matrix ang minultiply by C. Ano yun? So, lahat ng n rows mo, imumultiply mo by C. So, ilang beses mo in-apply yung theorem na ito? You have applied it to each of the rows. Ilang rows ba meron? N. Kaya yung extra factor mo is not just C, but C raised to the power of N. Kasi may C na N na Cs na lalabas.

**[2:22:18]** Did you understand? And again, by duality, whenever you do that to columns also, totoo pa rin yung mga theorems na ito, okay? So, sige nga, gawin nyo nga yung determinant na ito. Oh my god, what is that? What the fuck? Di ba? 3x3 nga, tapos biglang naging 3 digits ang hayop. Oo, ganyan, ganyan kahayop yung mga teacher ninyo. Pero, you know... Ang laloko lang yan. Sige nga, can you tell me what is the determinant? Oh my goodness.

**[2:22:59]** Sige, anong determinant yan? Sige, uigyan ko kayo ng time until you realize that the answer was really very simple. Sige nga. Think about it. Gamitin niyo yung mga brain cells ninyo to the fullest. without actually, kasi nobody likes to multiply. Nobody likes to multiply it like this, di ba? Gusto nyo bang gawin yan? Ayun na lang. I will not do that. Hmm. Pero pag napansin nyo yung napapansin ko, it should surprise you. Sige nga, ano-ano kaya yun?

**[2:23:39]** I will give you time, don't worry, sige, gawin nyo.

**[2:23:59]** I-type nyo lang yung sagot na sa chat box. Naku, nag-calculator na, an ba yan?

**[2:24:08]** Ano ko, iba sa inyo, nag-calculator na, tama ba?

**[2:24:21]** Okay, nakita ko yung gusto kong sagot. Okay, sagot ni student, yung row 3 po is 2 times ng row 1, 2 times ba? It's actually negative 2. Agree? Very good. Yeah, negative 2. As you can see, ito'y effect kapag yung row 3 minultiply mo by negative 2. Kaya yung negative 2 na extra factor na yan shall go out. And when it goes out, when it goes out guys, ang may iwanan ay isang matrix na may identical na rows. Anong sabi nung nakaraang corollary? When two rows of a matrix are identical, the determinant is zero, no matter what. Diba? So, that's negative 2 times 0, so the final determinant is just 0. Diba? This is a trick question.

**[2:25:23]** Kasi, 3 by 3 eh, parang ini-invite kayo na gamitin yung ano, yung down, down, down, up, up, up method. for us, hindi mo naman pala kailangan gawin yan. Kasi kapag ginawa mo yung down, down, down, up, up, up method, it's a trap. Nobody likes to multiply three three-digit numbers. Gusto nyo ginagawa yun? Kung gusto nyo, di isa kayong ano. Ewan ko kung anong trip yan. Diba? pagkanya-kanyang trip yan eh, nabahala kayo kung fetish nyong mag-multiply ng tatlong three-digit numbers by all means, gawin nyo maghapon. Diba? Kung na-excite kayo, pero ako, hindi. Wag nyo na akong idamay.

**[2:26:08]** Okay? Ayuntundihan ba yung example na ito? Okay, may tanong si sir. Are you curious to know? So marunong alam na natin ang effect kapag type 1, ano? Nagsichange lang ng sign. Pag type 2, namumultiply lang yung determinant by that scalar na minultiply, no? Are you curious to know kung anong nangyari pag nag-apply tayo ng type 3? tignan natin. Tignan natin in this example. I mean, this is a particular example but I want you to look at this as a general picture. Now, I don't want you to focus on this matrix. Tignan nyo yung effect ng type 3. Tignan nyo ha? Let's do it.

**[2:26:54]** Pag sinabi kong E313, yung row 3, ia-add ko sa 3 times row 1. Agree? Sabihin natin B yung sagot. Anong itsura ng B? Yung determinant ng B is actually like this, no? Tama ba? It's row 3, in-add ko yung 3 times nung row 1. Did you notice?

**[2:27:19]** Okay? Hello?

**[2:27:26]** Teka lang. Parang nadi-disconnect yata ako, hindi kong nakikita yung mga reactions. Nasusundan ba? Okay. Ito na. As we select one term from each row, kukuha at kukuha ka ng term dyan sa third column. Huwag nyong i-simplify guys ha. Do not simplify. I just like you to look at the form kasi I want you to think about this in general. When you eventually create your terms for the determinant, pipili at pipili ka sa third row na ito na may tigda dalawang terms. Do you agree? So ang itsura ng mga terms ng determinant mo is something from first row, something from the second row, and something from the third row that looks like this.

**[2:28:15]** Dalawang terms, okay? In algebra, we know that this product is actually a sum of two terms, ABC plus ABD. What I'm trying to say is, you can separate the determinant into two sums. Yung una, determinant muna nung part na ito at yung pangalawing determinant naman nung part na ito as it distributes. Agree? Mahati mo siya into two determinants. Kasi nga, ang reason, pag yung isang factor mo may dalawang terms, naahati siya into two terms.

**[2:29:01]** Do you agree? Naintindihan nyo, nai-imagine nyo, based on your experience in algebra, ayan, magiging ganyan. Okay, magiging ganyan siya. Fine. Okay. Did you see, did you see, na yung second determinant, second term, ay may common na factor na 3 sa third row? According to the previous corollary, previous theorem, you can factor it out. And the first term is precisely the determinant of A. And now, what can you say about the remaining determinant? That's the second term. It now has identical rows. And therefore, what? Its determinant is zero.

**[2:29:49]** So, the determinant of B is just the determinant of A.

**[2:29:59]** So, in short, sa totoo lang, walang effect itong 3 na ito. Kasi pag pinactor out mo siya, yung may iwan, identical rows, yung 0. So, the truth is, kahit na anong type 3 operation ang gawin mo, hindi pala nagbabago ang determinant. This is really surprising. Why? Kasi among the three operations, si type 3 ang pinaka-complicated guys. Diba? Yet, ano nangyari? Yet, siya yung may trivial effect sa determinant. Walang effect talaga. Just perform any type 3 operations, you are safe. Hindi magbabago ang determinant. Okay? Naintindihan? In symbols, if you perform a type 3 operation on rows or on columns, bahala ka, the determinant is left.

**[2:30:56]** Unchanged. Now, why all of a sudden bigla natin pinag-usapan yung effect ng type 1, type 2, at type 3 operations? Kasi ganito po. Did you remember, madaling kumuha ng determinant pag upper triangular yung matrix? eh kung hindi upper triangular yung matrix, pwede ka naman mag elementary row or column operations hanggang maging upper triangular sa A guys, diba? At kung nire-record mo yung mga steps na ginawa mo, marirecord mo kung paano magbabago yung determinant. Kaya nga, we have now just introduced a method for calculating determinants kahit na hindi ka 3 by 3. One method is to reduce your matrix or your determinant into an upper triangular matrix using elementary row or column.

**[2:31:50]** operations. And syempre, ito take note na yung mga changes dun sa determinant by knowing all the results in the previous slides. Makukuha nyo yung determinant ng original matrix. And to show you exactly that, meron akong example dito. Okay? Palagay ko yung natitirang time natin, eto lang yung gagawin natin. Kasi you know, mahirap gawin ito eh. Medyo maraming trabaho. But let me show you how it's done. Okay? Kinig mabuti ha? Are you ready to listen?

**[2:32:32]** Are you ready? Okay. Here it goes. Para ka lang mag-a-RREF, except ang goal mo lang ay maging upper triangular. You don't, your goal is not to turn this into RREF guys. Ang goal lang natin ay makakuha ng upper triangular so basically we would like to eliminate the things below the main diagonal. At syempre, ang una kong gagawin guys, hindi ko na i-type yung solution so I have to write it down. Pakikipagpalit ako ng row 1 at row 3. Kasi po, gusto ko ng 1 doon sa tuktok para madaling mag-eliminate. But by doing so guys, Remember, may negative one na lumalabas.

**[2:33:17]** Okay? Hello? Are you with me? So far? Sige ha, alright.

**[2:33:30]** Minsan, ilagay nyo lang ito. I mean, ilagay nyo lang ito para alam ko kung ano yung ginawa ninyo. You don't... Sa totoo lang, in practice, you don't have to write it there. Kaya lang, just to explain your side, para alam ng teacher ninyo kung anong ginawa nyo. Kung columns man, laging nyo ng C. Ibig sabihin, you're working with columns. Okay? Ito, pag type 3, You don't really have to write the operations. Ang kailangan nyo lang gawin, bilugan nyo, dagyan nyo ng asterisk, para alam ko na you are applying a type 3 operation, type 3 operations, and dahil wala namang effect yan sa determinant, you don't really have to write. Okay?

**[2:34:15]** Pero kung Kung gusto nyong isulat yung operations, okay lang din. Ako kasi as a matter of practice, hindi ko na siya sinusulat. Sa type 3 wala naman siyang effect, so there's really no need to write it there. Nakuha nyo? Pero paano ko i-eliminate sir? Ganito. Diba yung... 5-bottle row, hindi naman nagbabago, so I just write it one more time. Ito yung magbabago, magsisiro to. Pero, iti-change mo yung sign, multiply and add. Naalala niyan? Multiply and add, change the sign ha, 18 minus 3, 15. Hello, are you with me? Okay.

**[2:35:01]** Okay. Sige. You're still with me. 2 times 2, ah, 2 times negative 2 plus 2, negative 4 plus 2, negative 2. Okay? Next. Next what? 2 times 2 minus 5. negative 1. There you go. Diba? O, ito naman, to eliminate this dahil 1 ito parang sinusubtract lang yan eh, diba? Subtract mo, row 3 minus row 1, 0, 0, 0, oh my god! Ay, nag-zero?

**[2:35:48]** Anong ginawa ko? May mali akong ginawa. Kita nyo, may mali akong ginawa.

**[2:35:58]** Ay nako, when I place,

**[2:36:05]** I should have, oh tsang yan, bobo, no? Pinagpalit nga natin yung row 1 at routine, hindi nyo napansin, kinopia ko lang. Malamang magsisiro talaga, no? Ay nako. O Lord. Sa inyo, unang step pa lang, mali na ako. Sabi sa inyo, ganyang kahirap mag-determinant.

**[2:36:30]** Okay? Tama na ba? Pinagpalit natin yung row 1 at row 3 pero hindi ko pinagpalit. Tangangot. O sige, gawin natin ito. This time, in a negative 2 mo ito, diba? siyempre, mag-zero ito, sorry, mag-zero ito, negative 2 times 3 plus 5, negative 6 plus 5, negative 1.

**[2:36:59]** What the hell? 4 minus 3 is 1.

**[2:37:06]** There you go. negative 4, minus 2, negative 6. At ito naman to eliminate, you just add. Zero, nine, two, five. Are we good so far?

**[2:37:27]** Okay, ganito ha. Let's say naiilang ka may negative sign sa labas. Pwede mo ipasok yan. Sa ko ipapasok. Strategically, i-multiply ko yan sa third row. Why did I think about that? Ha? Para may pivot na tayo kagad na one. Did you understand? Tapos, mag-i-interchange na naman ako. shit na yan, no? Anong bayan? May negative na naman.

**[2:38:02]** Okay lang. Huwag na kayo umiyak. So, E1, 2, kasi ilalagay kayong 1 dun saan. Ay, hindi yung 1, 2, 3. So, may negative na naman sa labas. Okay, ganito ha. Isulat nyo ng buo yung negative 1 as a matter of tip kasi pag negative sign lang yung nilalabas nyo minsan na sasama siya dun sa equal sign nakakaligtaan nyo Based on experience, nakakaligtaan ng studyante pag negative sign lang yun nilalagay sa labas. Akala nila part nung equal sign, so na hindi siya nabibilang. Ikaw mag-ingat kayo. Okay? Hello? Are you listening?

**[2:38:50]** Kaya ako buo kong sinusulat yung negative one. para safe. Kasi prone to error, pag negative sign lang yung nasa labas, baka dumikit dun sa equal sign, hindi nyo makaligtaan nyo. Okay, next, I'm going to get this, now, hindi natin goal mag RREF, ang goal ko lang upper triangular, so ito lang yung i-eliminate ko.

**[2:39:16]** Gets? Hello. Gets ko na yan, pag nakita ko na nilagayin ng asterisk, no? Or at ng bilog. You don't have to write the operation at this point. Sige. Tuloy natin. Elimination. 1, 3, negative 2, 2. 0, 1, negative 1, 6, eto na, 0 pa rin to, eto 0, negative 15 ang multiplier ha, oh my god, 15 minus 213, OA, OA ka, ah, ah, negative, eto na nga, ayot na yan. negative 15 times 6. Oh, Lord. Negative, ano ba yan? Negative 90.

**[2:40:03]** Ayot, no? May negative 91 na lumabas. Tama ba? Shit. So, zero. Zero. Ito naman, negative 9 ang multiplier, ha? So, ganon. 9 plus 2, 11, let's check, nakakita na ako ng dilubyo. Kasi kung nagsama-sama sa iisan lugar yung 11, 13 at 91, parang ano, kinukulam ba ako? Ano yung pakiramdam yan? Parang may nangungulam sakin. O sige. negative 9 times 6, negative 54, hayop ka, buhay ka pa, plus 5, shit, negative 49. Kita nyo, nagkita-kita yung tatlong brisit, no?

**[2:40:50]** Ay, yung apat na brisit, nagkita-kita sa isang lugar, kasi alam nyo bakit ako Medyo natatakot dyan. Ba't ako natatakot dyan? Kasi po, wala lang. Ang papangit nila. Nakakaramdam ako ng mga fractioning.

**[2:41:11]** Naramdaman nyo ba yung nararamdaman ko? I don't know if you can feel what I feel.

**[2:41:21]** Take note, pwede rin kayong gumalaw ng mga columns, ha? Kaya lang, I mean, baka malito pa kayo. Pwede rin kayong magmanipulate ng mga columns, kaya lang it may be something new for you, kaya ingat kayo. Ang 91 ba divisible sa 13? I'd like to know, 91 divisible by 13, check na natin, putyang yan, 91 divided by 13, baka equals 7, o kita nyo, 7 palayot, tama! 7 times 13, 91 pala. O, kita nyo, hindi ko inaakala yun.

**[2:42:08]** Ang gagawin ko kasi guys, sa third row, i-factor ko yung 13 para magkaroon ako ng 1 doon. So when I do that, magiging negative 13 na sa labas. Tapos, magiging ganito.

**[2:42:27]** 1, negative 7. Nice!

**[2:42:37]** Gets nyo? Hello? Are you still with me? We're doing fine, no? Okay. Finally, 1 na to, papatayin ko na lang 11. Pag nagawa ko yun, tapos na. Shit! Katisaanit.

**[2:42:58]** Diba?

**[2:43:05]** Okay, so 0, 0, 0, that's the intention. Pero itong last na element, change the sign, negative 11 times negative 7, 77, shit, minus 49, hindi ko alam to, shit, ano ba to? Ayoko nung may borrow-borrow. Alam ko na. Ang gawin mo, mag-add ka ng 2, 79, add ka ng 2, 51. O, mas madali ito. 8, 28. O, kala niya ha. Ganyan ginagawa ko nung maliit ako eh. Pag may borrow na, ang ginagawa ko, Nagdadagdag ako na nagdadagdag hanggang mawala yung borrow.

**[2:43:53]** Anong ginawa ko? Nag-add ako ng 2.

**[2:43:58]** May ito mag-add ng 1? Ba't 2 ang in-add ko? Mag-add ka ng 1, magiging 78, eto magiging 50. O, mas madali pala to. Nakuha niya, you get the idea. Hindi ka magbabaro, kasi ang idea nun, pag ang dalawang numbers, nasa number line, ito yung difference nila. Pag nag-add ka naman ng same na number, let's say A plus 1, B plus 1, nagbabago ba yung distance nila? Hindi naman eh.

**[2:44:31]** I noticed this when I was in elementary school, kasi nga Galit na galit ako sa teacher ko pag nagbabaraw, lalo na yung 1,000 minus 739. Ang gusto ng teacher mo mangyari, yung teacher mong bugok, ang gusto niya mangyari, manghiram ka ng manghiram ng ganyan, di ba? Hindi ko naaalala yan. I mean... Bobong-bobo ko sa sarili ko nung ano, tinuturo yan. Hirap na hirap ang brain cells ko. Ang ginawa ko, nag-subtract ko ng tig-isa. So, 999 minus 738. O, di walang barow-barow. Ayop kang teacher, kaganon lang pala yun. Nakuha niya? Naintindihan niya? Oo, pwede mong palang ganun.

**[2:45:17]** Actually, ganyan ginagawa ko nung ano, nung maliit ako. Kasi alam nyo, ang arithmetic para sa akin noon, maliit pala akong mukha na akong pera. Ang iniisip ko mga pera yan, halimbawa isang libu yan, pabukasan mo ng 739, magkano magiging sukli? ang ginagawa ko, parehas lang yung sukulay kong 999 yung pera ko, pabukasan ko ng 738. Lahat ng ano, ng math ko noon, tungkol sa pera lang, kasi maliit pa kumukha na akong pera.

**[2:45:47]** O diba? Kasi pag pera yan, nakakalculate mo. Ang bilis ko kapag pera. gano'n na, re-realize ko kapag ano, bagal ko, kapag numbers lang talaga, bagal ko dyan. So, ano na nato? 77 minus 49, kunyeta, nakalimutan ko na. 78 minus 50, 28. O, so yung dulo ay 28. Ganun ba yun? Hello, guys! Were you able to follow? Tapos na tayo, oh. Ngayong upper triangular na tayo ay magdiwang kasi ang determinant nyan, mumultiply mo lang yung maraming 1 tsaka yung 28 sa dulo which is by the way, hindi ko na naman alam kung paano gawin.

**[2:46:36]** Oh my good lord, itong linear algebra. Isa to sa mga part ng linear algebra na ayoko. Ano ba to? 28 times 13.

**[2:46:48]** Ilan ba ang tatlong 28? Tatlong 28 ay 84, di ba?

**[2:47:04]** Ito ay 64 ba?

**[2:47:12]** Tama ba? Can you please confirm? Sige, negative 364 on the terminal. Ako, inaka-ban ako. I-calculator nga natin. Oh my goodness. Pag ito hindi negative 364, magre-resign ako. O tsaka, pinagod mo ako. Sige. 4x4, tapos biglang ano-ano, hindi nga, oh my good lord, magre-resign ako. Sige. Nagayin natin yung sagot, ano yung sagot? 2, 5, negative 3, negative 2, negative 2, negative 3, 2, negative 5, 1, 3. Nakaba na ako. Mag-resign ako bigla.

**[2:48:05]** Negative 1, 6, 4, 3. Bye bye guys! Kita nyo, ano sa gap? Negative 160, ang layo ng sagot natin. Bye! Wala na kayong teacher. Hindi ko alam saan tayo nagkamali. Sabi ko sa inyo hanggang 1.30 ito lang yung gagawin natin eh. Oh my good Lord! Where did...

**[2:48:41]** Shit! Anong gagawin natin? Tanong nga natin kay Gemini. 2 times 3 minus 3, saan mo nakuha yan? 2 times 3 minus 3, 2

**[2:48:57]** times 3 minus 3, po, tsang yung sa una pa lang,

**[2:49:06]** ano ba yan?

**[2:49:12]** Wait lang, wait lang, taga lang, screenshot natin to, para alalahanin natin yung araw na to. hindi, charot. Ang gagawin natin, tuturuan ko kayo paano mag-review gamit si Gemini, ha? May Gemini ba ako dito? Sa iPad ko? I don't know.

**[2:49:36]** Ay, wala akong Gemini. I'm a very honest citizen. Charot. Ano bang AI ko dito? Wala ba ako AI? Wala akong naka-install yata eh. Buti pa yung emulator ng Gameboy meron dito eh. Charot. Ah, ano ba to? Ano ba meron dito? Wala akong AI dito. Bobo tong ano eh? Siri AI? Ay, hindi ito yun. Bobo yan si Siri eh. Ayoko gamitin yan. Gemini, sino? Gemini. Baka pwedeng diretsyo na sa website.

**[2:50:18]** Sige, new chat. Ask Gemini. Upload.

**[2:50:26]** Auto. Okay. Ito ba yun? Auto.

**[2:50:38]** Where did we get Where do I got? Hindi ko alam tamang English. Where? What the fuck? English na lang. Ano ka natin dito, saan ako nagkamali?

**[2:51:00]** Please correct.

**[2:51:10]** Oo, nagkamali ka sa pangalabang step nung ginawa mong zero ang mga elemento sa ilalim ng pivot one. Hindi ko na itindihan. Nagkamali ka sa pangalawang step, nung ginawa mong zero ang mga elemento sa ilalim ng... Okay. Pangalawang matrix, ang unang row ay 1, 3, negative 2. Nung ginamit mo ito para gawing zero, dapat 3, negative 2, Negative 1. Ah, ito yung sinasabi kanina ni ano, ano? Kaya lang, Diyos ko, hula na tayong time.

**[2:51:49]** Oh my good Lord! Sabi sa inyo, pag may mali, sasabihin nyo kaagad eh.

**[2:51:58]** Hindi to 15, no? Shit. Can I just quickly do it?

**[2:52:09]** Sundan nyo ng mata nyo, ha? bilisan nyo. Kasi alam nyo, mali na yan lahat pag mali ka sa umpisa. Ayup! Ayup! Ito ay 3, saan ang galing yung 15 mo? Hindi ko naintindihan saan ang galing yun? Ano ba nang galing yun? Nainis ako? High blood? Hagi na nga. Sige, yung negative 1, pinasok natin yan eh. Diba? Pinasok natin yun para maging 1 to.

**[2:52:50]** Yan, ganyan. Bino mong haba-haba ng airtime natin, mali naman no? But I hope you get the idea. Sana kuha niya idea, tapos magro-row, ano tayo, interchange ulit. So, may negative one ka ulit sa labas. Sana pala hindi ko na binura lahat. Nagsisi ako bigla. Kasi may mga nare-retain naman, diba? Tapos, from here, eliminate ko tong dalawa. Okay. Magiging... abulin ko yung oras. sundan nyo na lang ha, 0, 0, 2, ah ay, mali, bobo, bobo, bobo, one yan, tama ba?

**[2:53:43]** Negative 19,

**[2:53:49]** sige, 0, 0, 11,

**[2:53:57]** negative 49, ganun ba yon?

**[2:54:09]** Sige. Tama. Buti na lang, mas madali yata ito, no? Negative 1. Tama, no? Am I doing good so far?

**[2:54:31]** Zero, okay. Negative 11 times negative 19 minus 49.

**[2:54:41]** Putang yan. Ano ba to? Oh, 209.

**[2:54:51]** Ay, ang galing. Dumabas yung gusto nating sagot. Nag-adjust dahil sa calculator eh, no? Ay, naka. Ina-adjust ang buhay dahil sa calculator. Kita nyo. Kahit ako hindi ko mapaperfect yung long exam number 1 dahil sa ganito eh.

**[2:55:14]** negative 160. Pero alam nyo, ito'y efficient, kasi elementary row operations are efficient, lalo sa computing in terms of sa point of view ng computing power ng mga computer, efficient na efficient ang mga row operations. Pero may mas mabilis akong method na ituturo sa inyo next meeting na yung method na yun yung kombinasyon ng row operation tsaka nung isa pang method na ano, na ituturo ko next meeting. Pag pinagsama nyo yung dalawang method, kasi yung another method, yung next method na ituturo ko sa inyo for calculating the terminal, hindi sya necessarily faster than the old one. Itong reduction to upper triangular, it's not necessarily faster.

**[2:56:10]** Pero pag pinagsama mo yung dalawang method na yun, yun yung mas mabilis. Meron pa palang isa. Kaya kaya natin ito ng 2 minutes?

**[2:56:24]** Sige, assignment ito. Try nyo ito ha. Try this. Dito tayo magsisimula ang next meeting, so you can check your work. And ano ba susunod? Ah, okay. Hindi pa pala natin ito nasasagot. Ba't natin kailangan pag-aralan ng determinants? Kasi we will prove. Next meeting, bakit nga ba? Kasi the determinant determines if a matrix is non-singular. Once daw na ang determinant na na-compute mo, hindi zero, ang laki ng margin, basta hindi zero, non-singular. Kaya nga, maidadagdag natin yan, ah, wag nyo na muna pansinin ito, ito yata yung proof. Kaya, maidatagdag natin sa listahan, ito.

**[2:57:16]** Naalala nyo yung unifying theorem? Set of five statements? Ito sila originally, meron ka ng pang-anim ngayon. Kung gusto mong gamitin ang determinant to determinant singularity, meron tayong condition, kailangan yung determinant, hindi zero. So nakadagdag tayo ng one more statement after this lesson. Kung gusto mo in terms of linear system, ganito. In terms of homogenous linear systems, ganito. In terms of RREF, ganito. In terms of elementary matrices, ganito. In terms of determinant, ito yung condition para ang matrix ay non-singular. Nice na?

**[2:58:03]** Nakuha nyo? O, naka 6 over 20 na tayo, so iksabihin talagang mag-one third na tayo off the way, kaya maglalong exam 1 na eh, okay? We will just continue from here, next meeting, okay? I don't know if, so next meeting will not be the exam yet, no? Maikli na lang yung natitirang lesson guys. Don't worry, may clean na lang yun, kasi isang method na lang, tapos na. Okay? And with that, i-off ko na yung recording.

