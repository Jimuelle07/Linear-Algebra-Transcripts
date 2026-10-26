# MATH 018 Online Class: Determinant Theorem, Cofactor Expansion, Adjugate & Cramer's Rule (Transcript)
Instructor: professor. Recording is about 2 hr 36 min long. The transcript is in Taglish, as spoken (auto-transcribed with Whisper large-v3-turbo; expect occasional mishearings).

## Topics covered
- Assignment from last meeting solved: a 4×4 with a on the diagonal and b everywhere else (a, b arbitrary and possibly 0, so you can't factor out a to get a pivot). Add rows 2–4 to row 1 (type 3, det unchanged), factor out a + 3b, eliminate: det = (a + 3b)(a − b)³. Check with a = 3, b = 2: 9 · 1³ = 9 (the calculator agrees)
- Main theorem: a square matrix A is non-singular ⇔ det(A) ≠ 0. The determinant "determines" non-singularity without computing an inverse
- Aside: singular matrices are "dense" (every small neighborhood of a matrix, measured with a matrix norm, contains a singular one), so floating-point rounding (2 → 2.001) can flip singularity (ill-posed problems). Application: coding theory and error-correcting codes (scratched CDs, Hamming code)
- Lemma: det(EB) = det(E)·det(B) for any elementary matrix E, proved type by type. det(Eᵢⱼ) = −1, det(Eᵢ(α)) = α ≠ 0, det(Eᵢⱼ(α)) = 1, so an elementary matrix never has det 0
- Proof of the main theorem: non-singular A = E₁⋯Eₖ, so det A is a product of non-zero numbers. Singular A: its RREF B ≠ I has a zero row, so 0 = det B = det(Eₖ⋯E₁)·det A, which forces det A = 0
- Statement 6 added to the unifying theorem: A non-singular ⇔ det(A) ≠ 0 ("6 over 20" statements)
- det(AB) = det(A)·det(B) for any n×n A, B (multiplicative), extending to any number of factors. Proof by cases: A non-singular; A singular ⇒ AB singular (sub-cases B singular, and B non-singular using x = B⁻¹y where Ay = 0)
- The determinant is NOT additive: det(A + B) ≠ det A + det B in general. 2×2 counterexample: A + B = 0 (det 0), but det A + det B = −1 + (−1) = −2
- Corollary: if A is non-singular, det(A⁻¹) = 1/det(A) (take det of A A⁻¹ = I). E.g. det A = 2 ⇒ det A⁻¹ = 1/2, with no need to find A⁻¹
- Cofactor (Laplace) expansion: group the terms of det A by which entry of row i they use: det A = Σⱼ aᵢⱼ × (cofactor of aᵢⱼ), written Aᵢⱼ with a C on top (a different notation from the old uploaded notes). Works along any column too (duality). Best on a row or column with many zeros
- Cofactor formula: cofactor of aᵢⱼ = (−1)^(i+j)·det(Mᵢⱼ), where Mᵢⱼ is A with row i and column j deleted. The sign comes from (j − 1) column swaps plus (i − 1) row swaps that move aᵢⱼ to the (1,1) position. (−1)^(i+j) is the + − + − checkerboard pattern
- 4×4 example (rows 2 −1 3 5 / 2 0 1 0 / 6 1 3 4 / −7 3 −2 8): plain expansion along row 2 gives two 3×3s. His "mixed method": C1 → C1 − 2C3, expand along row 2, then C3 → C3 − 4C2 and expand again down to a 2×2: det = −(16 + 27) = −43 (the calculator confirms)
- 5×5 sparse example: keep expanding along a column with a single non-zero entry (column 2, then column 4, then column 2) down to |4 5; 6 7| = 28 − 30 = −2, so det = 6·(−2) = −12. Exam style: his problems (including a 5×5) test properties and concepts, not heavy arithmetic, and he writes them himself
- Find λ so that λI − A is singular, A = [[3,0,3],[0,3,0],[3,0,3]]: det = (λ − 3)[(λ − 3)² − 9] = 0, a difference of squares, so λ = 0, 3, 6. These are the eigenvalues of A (the "DNA" of a matrix, a future topic). His screen share crashed at about 1:45
- Adjugate (he prefers that name over "adjoint"): adj A = transpose of the matrix of cofactors. A·adj A = det(A)·I (off-diagonal entries are expansions of a matrix with two equal rows, so 0), hence A⁻¹ = (1/det A)·adj A. Asked by a student in another section on MS Teams. Impractical; Gauss-Jordan on [A | I] stays the "gold standard"
- 2×2 inverse: A⁻¹ = (1/(ad − bc))·[[d, −b], [−c, a]] (swap the diagonal, negate the other two). Example A = [[6,9],[6,7]]: det = 42 − 54 = −12, A⁻¹ = −(1/12)·[[7, −9], [−6, 6]] = [[−7/12, 3/4], [1/2, −1/2]]
- 3×3 example A = [[2,0,−1],[1,1,0],[0,−2,3]]: C1 → C1 − C2, then expand: det = 6 − (−2) = 8, so A is non-singular. adj A = [[3,2,1],[−3,6,−1],[−2,4,2]], checked by A·adj A = 8I, and A⁻¹ = (1/8)·adj A. A 4×4 would need sixteen 3×3 determinants
- Cramer's rule: if A is square and non-singular, Ax = b has xⱼ = det(Aⱼ)/det(A), where Aⱼ is A with column j replaced by b (follows from x = (1/det A)·adj A·b). Example A = [[2,3],[1,2]], b = (2, 0): det A = 1, x₁ = 4, x₂ = −2 (check: 8 − 6 = 2, 4 − 4 = 0). Rarely used in practice; Gauss-Jordan/RREF works even when A is singular or not square
- Long Exam 1: its coverage ends with this lesson. Class dismissed early (making up for recent overtime). Next week he will give the exam guidelines (what to bring, when and where, pen and paper), so don't be absent, and start the next lesson (not in LE1). Calculators: classroom ones usually lack a det function, and even if calculators are allowed he will still look for your solutions

## Transcript
**[00:05]** So, we are now, or the session is being recorded right now. Okay? Saan ba tayo natapos last time? So, let me check the slides. Available. Oh! I think this was task as an assignment. Diba, I ask you to try this at home? Kung kaya ninyong, ah, naalala nyo? Ito yung huli kong sabi ko, try ninyong gawin sa bahay. Were you able to do this? This is a little bit tricky, no? At this point, so, So, let me share to you kung paano ko gagawin ito as, let's say, as a student. Paano ba in-evaluate yung determinant na ito?

**[00:57]** First of all, mapapansin ninyo yung determinant na ito ang size ay 4 by 4. So, lahat ng mga techniques na tinuro ko sa inyo yung yung puro down, down, down, up, up, up method. Hindi yun gagana. Okay? Hindi gagana yung down, down, arrows, up, arrows method na they will not compute the correct determinant. So, paano ito ginagawa? Ang alam lang natin ng method At this point ay yung reducing the determinant into an upper triangular determinant, diba? Tapos gumagamit tayo ng mga row operation, row or column operations. Do you remember that? Yun yung ating natutuhan last time.

**[01:42]** Today may maaaral tayong panibagong method, huwag kayong mag-alala. Pero it is not a better method, it's just an alternative method. But for this example, paano ba ito inevaluate? Now yung A and B here represents arbitrary scalars. They are not even required to be non-zero, but pwedeng zero yung mga yan, no? Doesn't matter. Basta si ANB are arbitrary scalar. Kasi, bakit ko kailangang banggitin na hindi sila kailangang non-zero? Kasi, One may think, pwede isipin ng isang student na gusto ko ng 1, gusto ko ng pivot dito sa 1-1 position so I can eliminate all the Bs.

**[02:31]** So sigurong may isip niya parang i-factor yung A sa first row para magkaroon ng ganon. Kaya lang guys, When you do this, when you do this, this is correct except yung a dito is not necessarily non-zero, pe pwede siyang zero. When you do this, you are under the assumption that a is non-zero. Right? Eh wala namang assumption na hindi zero si A, so you cannot do this. Okay? So you cannot. Anong gagawin natin? O di magka-cry-cry na lang kasi hindi mo na alam kung anong gagawin natin. Paano ba ginagawa ito? Well, pansinin ninyo, kapag in-add mo lahat ng mga bagay na nandito sa bawat column, iisa lang, no?

**[03:20]** A plus 3B. Did you notice? Diba? Pag in-add nyo itong lahat,

**[03:29]** A plus 3B. Actually, ang gagawin ni Sir, ang gagawin ni sir. Ang unang step na gagawin ko, kapalitan ko yung first row, ia-add ko yung second row sa kanya. Ia-add ko lang talaga. Ang ibig sabihin nun ng E1 to 1, ia-add ko yung first row sa second row, lalagay ko sa first row. second row muna. Kapag ginawa mo yun, magiging A plus B, B plus A, 2B, 2B, right? So pag na-add ko na ngayon yung second row, ia-add ko naman yung third row sa first row.

**[04:16]** Diba? E131 naman. Wala namang effect sa determinant kapag type 3 operations ang ginagawa natin, so walang nagbabago. So if you now add the third row to the first row, you will get A plus A plus what?

**[04:37]** A plus 2B 2B plus A, or A plus 2B na rin. Sige. A plus 2B, 3B. Tapos B, A, B,

**[05:00]** A. Finally, i-add ko yung first row sa last row, which is the fourth row. Nakuha niya. Ang effect nun, yung sum nung lahat ng rows na ilagay ko sa first row. Do you agree? Guys, do you agree? Yan yung mangyayari, no? Oh, why, why would I do that? No, I mean,

**[05:32]** why would one do that? Ang gagawin ko kasi guys, dahil pare-parehas ng A plus 3B yung nasa first row, I can somehow factor it out. Magkakaroon ako ng maraming one.

**[05:50]** Pag kasi meron akong one dyan, guys, pwede ko nang gamitin yan to eliminate things,

**[06:04]** gets, gets niya ba? Yan. Ang i-apply natin ay, para ma-eliminate ay E21 negative B, E31 negative B, saka E41 negative B, okay? So magiging A plus 3B, so ito 1, 1, 1, 1, it remains as that. Pagkatapos ito magiging 0, A minus B, at A minus B po yun, ha? Bakit po A minus B yun? Kasi, negative B plus A, no?

**[06:46]** Yung negative na ito mo multiply doon pa ganun. Okay? Gets? Tapos, ito naman, negative B plus B zero, negative B plus B zero, zero, zero, A minus B. Then, 0, 0, 0, 0, and A minus B. Magic ba? Magic na? Naging upper triangular na siya kaagad.

**[07:26]** So, in short, imumultiply na lang natin yung main diagonal elements. So, ang kalalabasan, a plus 3b times a minus b to the power of 3 or cubed. So, that's the determinant. Gets? Halimbawa, for example, sa traditional example, nakakita kayo ng matrix, let's say, 3, 2, 2, 2, 2, 2, 3, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 3, 2, 2, 2, 2, 2, 3, 2. Naray ganyan. O, ayan na yung formula. No? Gets nyo ba?

**[08:08]** It's going to be 3 plus 3 times 2. times 3 minus 2 cubed. Agree? It's going to be 9. Is that correct? 9 nga ba? Maybe we can use a calculator to verify our answer. I mean, check natin kung yung formula natin ay nagana, no? Determinant.

**[08:45]** So, 3, 2, 2, 2, 2, 2, 3, 3, ay! This is 2, 2, 2, 2, 3, 2, 2, 2, 2, 2, 2, 3. Surprise! Tama tayo. Nakuha niya. the determinant is actually equal to 9,

**[09:17]** okay? I know there may be many ways. There may be other ways to compute the same determinant, no? This is not the only way, but I mean... This is how I would do that. I would do this problem. There may be other solutions that you may do, no? As long as they are correct, walang reason para hindi ko tanggapin yung sagot na iyon. Pero definitely, isa lang yung kalalabasang answer. Ito lang yung sagot. Kung mag-iba man ang itsura ng sagot ninyo, possible na nakamultiply ito. Did you understand? Hindi siya nakafactor kagaya dyan. yun lang.

**[10:05]** So, nasa ano ba tayo? Nasa portion na tayo where we ask, bakit pa natin inaaral ang determinants in the first place? Kasi, in this lesson, the main theorem or the main idea is this theorem. This theorem says, that the square matrix A can be said to be non-singular if and only if its determinant is non-zero. So in other words, the determinant is basically a check, no? A non-singularity check. sinitcheck ng determinant kung yung isang matrix ay non-singular without really having to produce an inverse.

**[10:51]** Kasi diba by definition, pag sinabi natin yung non-singular, may inverse. Karaniwan, hindi madaling maghanap ng inverse. An alternative to that, Kung gusto mo lang malaman whether a matrix is non-singular or not, what you may want to do is to get the determinant. Once you found out that the determinant is non-zero, once na makita mo yun on determinant 5, on determinant 4, Lahat yun non-singular. Nagiging singular ka lamang when you found out that the determinant is zero, okay?

**[11:36]** Tama? Now, you may think na, isipin, parang isipin mo, Ah, mas marami ang mga non-singular, no? Kasi, mas maraming options for the determinant as long as the determinant is not zero. Non-singular, correct? Pero, actually, this is counterintuitive but let me tell you, sa pag nag-aral kayo ng advanced linear algebra. Although, although, isang determinant lang ang nagkokorespond sa mga singular matrices which are zeros, no? The truth is, mas dense ang mga singular matrices versus yung mga non-singular matrix. Anong ibig sabihin ng mas dense?

**[12:25]** Paano ko ba sasabihin, paano ko ba ikikwento ito sa inyo ng buong, ng, ng, in an elementary way? So, ganito. Imaginin mo ang mga matrices ay mga points sa space. Halimbawa, isang point sa plane, it corresponds to one matrix. Of course, how many matrices are there? There are infinitely many. Now, sa advanced linear algebra, when you study linear algebra, in a more advanced setting, mapapag-aralan nyo kung paano sukatin ang distance between two matrices. Meron ding paraan to measure distance between, ito yung matrix A, ito yung matrix B. May tinatawag na matrix norm.

**[13:06]** Ang notation namin tatlong ganyan. Ibig sabihin ng tatlong ganyan ay ang sinusukat natin ng norm ay norm ng matrices, hindi ng vectors, okay? May tinatawag na matrix norms. But of course, I will not be talking about matrix norms at this level kasi the concept is quite hard to understand. Basically, what this difference measure is their distance. It's the distance between two matrices. Kung gaano sila kalapit sa isa't isa. Syempre, pag yung number na yan ay maliit, ibig sabihin yung distansya nila ay maliit. Now, there is one theorem in Advanced Linear Algebra, that if you take an arbitrary matrix, let's say a random matrix A, and you know guys, pag nag-drawing ka ng circle around it with A being the center, no matter how small the radius is, kunwari gano, let's say ang radius nya ay kunwari epsilon.

**[14:04]** kapag gumawa ka ng maliit na maliit na circle, according to that theorem, laging may nage-exist na singular matrix na S sa loob ng neighborhood na yan. No matter how small epsilon is. Ibig sabihin, Kapag yung epsilon mas pinaliit mo pa, let's say you made the circle even smaller, lagi at laging may mag-e-exist na singular matrix sa loob. Nagigets ninyo? So in other words, Sa paligid ng isang matrix, napakaraming singular matrices. Kaya you may think na marami ang mga non-singular matrices.

**[14:48]** Yes, marami sila, but in reality, mas dense yung mga singular matrices. Nakakalat sila sa kung saan-saan. Ang sinasabi ni sir, Bakit ko sinasabi sa inyo to? Kasi diba, ang desirable na uri ng matrix sa linear algebra, mga non-singular, kasi they are the reversible matrices. Nare-reverse natin yung effect nila. Why do I have to tell you all of this as computer science students? Kasi later on, when you study numerical mathematics or whatever, saan nyo ba dapat pag-aralan ko? Meron kang matrix, for example, na gagamitin. I don't know, manghula lang ako. Kunwari may entry ka dito, 5, 4, negative 1.

**[15:33]** 0, 4, 2, 3, 5, let's say, 0. Okay, kung nari yung matrix na ito. And let's say you found out that the determinant is not zero. Hindi ko alam kung ano yung determinant ha, kung nari nilang ito yung non-singular. Alam nyo ba, because of that property, ibig sabihin yan, magkaroon ka lang ng kaunting rounding error sa mga entries nyan. Let's say yung 2, ginawa mong 2.1, as the computers will normally do. Remember, do you remember how computers process information? Hindi yan nag-a-add talaga the way humans add. gumagamit ang computer ng float system.

**[16:16]** 64-bit yata yung ginagamit natin ng mga computers nowadays, but kakaiba yung arithmetic ng computer in comparison to the human arithmetic. In fact, may dun sa system na yun, may largest float lang. hindi lahat ng numbers ay kayang i-display or kayang ilagay sa memory ng computer. Wala kasing infinite sa memory ng computer. Understand? So, ang sinasabi ko, may chance na kapag yung, let's say, nagko-compute ka ng matrices, Dahil sa maraming operation, nagkaroon ng rounding error because of the float operations. Instead na maging 2, naging 2.001.

**[17:01]** Alam nyo ba dahil sa .001 na yun, kahit dahil maliit na maliit yan, possible na maging singular yung matrix nyo because of that at magkakaroon ng error. It happens, no? Minsan, ma-experience nyo ito kapag kayo'y gumagamit na ng computers, let's say ng Python, o kaya ng mga calculators, GeoGebra. Minsan, when you do a very complicated matrix operation, makikita nyo, yung computer nagdi-display ng 2.001 kahit na dapat 2 lang yung nararoon. Kasi nga dahil yun sa mga errors na nangyayari, dahil ikakaiba yung arithmetic ng computers. Hindi siya pareho nung arithmetic natin.

**[17:52]** In particular, sa multiplication. Nagkakaproblema ang computer sa multiplication, especially pag decimal. And sa division, of course. Kasi yung division, multiplication lang naman din eh. So the way we multiply decimals in as humans is not the same way computers will multiply them. Magkaiba. I cannot tell you that enough, but I hope that you understand. It may happen, kaya ako kinikwento lahat sa inyo to, para hindi kayo magtataka bakit minsan ang computer pag nag-compute ako ng malaking matrix. instead na 2 yung in-expect ko, ang dinidisplay niya 2.001, naging singular tuloy yung matrix ko, imbis na non-singular sana siya na, yun, yun ang danger.

**[18:43]** Dahil dun sa property na yun na diniscuss ko kanina, na maraming mga singular matrices na nakakalat, because of that, sa applications, nagiging problema siya. Okay? Ibig sabihin, pag meron kang isang problema na sinosolve at nangyayari yun, ibig sabihin yung problem mo is ill post, when you say ill post, kaunting perturbations lang dun sa data, nag-iiba yung conclusion. Did you understand? Let's say, pinag-uusapan natin, let's say, nagtatransmit ka ng data from the moon to back to the earth. Let's say, may astronaut na-transmit yung data na yan, for example.

**[19:29]** Paano pag nagkaroon ng error? Delikado ko. Let's say, ang tanong, ang tanong, for example, ng astronaut ay, pasasabugi na ba yung buwan? Siyempre, ang sagot mo, no. Imbis na mapadala ng computer 0, yung napadala nyo 1, yung isang bit nagpalit, no? That's very dangerous. But of course, meron na tayong mga mathematics at tsaka mga code designs na tinatawag para hindi mangyari yung mga ganong klaseng. bagay. Alam nyo saan inaaral yan? Inaaral namin yan sa, may subject sa matang pangalan ay coding theory. Yung coding theory it's a math, pero ang application niya ay sa computer science na, Sa coding theory, pinag-aaralan kung paano, gamit ang linear algebra, no?

**[20:16]** Pinag-aaralan dun kung paano mag-design ng code so that kung magkaroon man ng konting perturbation dun sa data, no? Upon transmission. Nangyayari kasi may mga noisy channels na tinatawag. may mga channels na noisy, so yung mga bits ninyo, randomly, yung 1 nagiging 0, yung mga 0 nagiging 1. Because of that, nagbabago yung information. Paano natin, paano tayo gagawa ng code? So that, madidetect yung error, at the same time, makokorekt yung error. Isa yan sa mga applications ng linear algebra, mind you. So for example, you may look at coding theory, sa Wikipedia na lang.

**[21:00]** Ayun o, coding theory and cryptography.

**[21:06]** So simula, it may look like a computer science thing. Yes, it's a computer science thing kasi yun ang kanyang basis, no? But, it's really a math subject, no?

**[21:23]** Ayan. Ang subject na ito ay pinagsama-samang linear algebra, probability, isa to sa mga applications ng ano,

**[21:35]** Ano ba dito? Ano tayo ng error correction code? Ito, ayan. Ito yung basic na ano nyo na yun. Ano magsabi ng error correction codes? Alam ninyo kung paano gumagana yung mga CD natin. Ano yung CD player? Diba may mga CD tayo noon? Storage ng data, tapos. paano tayo nakakapag-save ng mp3? Ini-encode yun dun sa ano, sa gilid ng CD, dun naka-encode yung information. Tapos diba, kapag yung CD, have you experienced that? Kapag may gasgas yung CD, minsan tumatalon yung player. hindi tumatalon yung player, tumatalon yung tugtog, pero nagpapatuloy pa rin siya.

**[22:21]** Pag tumalon siya, ibig sabihin na detect nung computer yung error, may noise, may noisy channel kasi may scratch yung CD, nagdetect nga na may error, Pero, na-correct niya kasi tumuloy-tuloy pa rin naman yung kanta. Basically, tungkol dito yung coding theory. Ayan, nakita nyo ano? May mga, may mga linear algebra na part, no? Kung paano dinidesign yung mga yan. This is a very interesting subject, especially for you guys na nasa computer science. If you really want to do math at the same time, do computer science. This is a very good place to put your work, put your effort para mag-work. I mean, baka sa thesis ninyo, pwede nyong arali nito, maraming iba-ibang uri ng code, but in particular, ang pinakasikat na uri ng code, yung hamming code. Yung hamming code is a linear code.

**[23:22]** Ibig sabihin, gumagamit ito ng linear algebra. Yun yung ginamit natin nun, nung time na nagpadala tayo ng tao sa moon for the first time. Yung hamming code na tinatawag. yun yung ating ginamit na system, yun yung ginamit ng NASA to encode information para makapag-communicate yung mga nasa buwan. Pabalik sa, imagine na. Relatively new itong area na ito but, um, ayan o, may mga matrices right. matrix multiplication, kaya dapat marunong kayo ng matrix multiplication.

**[24:09]** Paano nako-correct yung error? You may want to study it, if you have time. Kaya lang kasi, ang subject natin yung linear algebra, so, I mean, I know that this is an application, kaya nga binabanggit ko sa inyo, pero, We don't really have the luxury of time to focus on one particular application. Pero nababangit ko sa inyo para kung meron kayong time at interested kayo to study, marami kayong pwedeng aralin.

**[24:42]** Okay? Layo na naabot natin, no? Dahil dito sa main theorem na ito. Okay. So basically, the theorem says, or this theorem kaya ito tinawag na main theorem, kasi it justifies the name determinant. Kaya siya tinawag na determinant, kasi guys, it determines whether a matrix is non-singular or not. Ang condition, dapat yung determinant ay hindi zero. So the question is, paano ba natin ito ipoprove? Paano ba natin mapapatunayan ito? Ito yung mga times na, diba karaniwan pag may mga proofs na complicated nilalaktawan ko?

**[25:27]** But I think this one is going to be an exception kasi I believe that you really have to see the proof kasi you will learn some insights from it. Na? Ready na ba kayo makinig? Are you ready to listen kung paano ko i-explain bakit ito magiging totoo? Okay, so let me explain. Ang unang gagawin natin, in order to prove the main theorem, so syempre hindi ito ganun kasimpling i-prove, meron muna tayong unang ipapakita. Ipuprove muna natin that if E is an elementary matrix na n by n, tapos meron akong matrix B na n by n din naman.

**[26:07]** So, ipapakita muna natin na ang determinant ng E times B ay pareho so determinant ng E times determinant ng B. Ulit, ano nga ang elementary matrix? Elementary matrix is basically like an identity matrix where you applied one elementary row operation only. Ano mang operation nang i-apply mo, it doesn't matter as long as it's an elementary matrix. the determinant of E times B is equal to the determinant of E times the determinant of B. Paano natin muna i-justify ito? Siyempre, dahil may tatlong uri ng elementary matrix guys, hatiin natin ito into 3 cases. kapag type 1, type 2, type 3. Kaya nga ito yung case number 1.

**[27:00]** Kapag si EI type 1, EIJ, anong ginagawa ng EIJ? Pag minultiply mo siya sa B, ang effect niya, pagpapalitin niya lang yung dalawang rows ng B. So in short ito, ito yung original na B. Pag minultiply mo na yung EIJ sa unahan, ang ginawa na neto, parang si B lang ito, nagkapalit lang yung row i tsaka row j. Now, what do we know kapag nagpalit ang dalawang rows? Nagpapalit yung determinant ng sign, right? Did you remember that from last meeting's lecture? So, isusulat natin yung determinant na yan as the negative of the determinant of B.

**[27:43]** But you know, dahil ang determinant ng identity ay 1, anong determinant nung EIJ? Ang EIJ kasi nanggaling sa identity by switching two rows also. So, kung ang determinant ng identity ay 1, dapat ang determinant ng Eij, negative 1 coming from 1. If you look at this equation carefully, yung negative sign dito, it corresponds to a multiplication of negative 1, right? Kaya pwede mong isulat. na yung determinant ng EB is negative 1 times depth B, tapos yung negative 1 na yan now accounts for the determinant of E.

**[28:24]** So, totoo na ito, in the case when E is a type 1 elementary matrix. Nag-gets nyo yung case 1? O, diba? Okay, paano ka pag-type 2? Pag-type 2 naman, ganito ang itsura ng elementary matrix ninyo. Ito yung original na B, pag minultiply mo siya dito sa kaliwa, yung row i, namumultiply by C. Do you remember the effect of that dun sa determinant? Yung buong determinant, is just multiplied by the factor C, okay? Now, coming from the identity which has determinant 1, ang determinant dapat ng EIC should be C times 1 or C. Kasi minultiply mo yung identity by C on the it row. Okay, so C times 1. So C yung determinant niya.

**[29:20]** Kaya yung extra factor na C na yun will now account for that determinant of E. So once again, this was proven to be true in the case when the matrix is a type 2 elementary matrix. Guess what? Kapag type 3, if E is a type 3 matrix, ang effect naman neto sa determinant ng B ay wala. So, di ba? Kapag type 3 walang effect. So it remains as the determinant of B. Kung ang determinant ng identity ay 1, anong determinant ng EIJ? syempre, 1 pa rin kasi wala kang babaguin sa determinant o identity.

**[30:02]** Nag-type 3 ka lang naman. Okay? Kaya yung the fact na determinant of B ito parang may extra na 1 dyan, di ba? It accounts for that case. Kaya nga, totoo na yung equation na ito for any elementary matrix B. So, napakita na natin yung highlighted na portion. Were you able to follow? Were you able to follow? Okay, tingnan nyo ito. So, undetermined ng remark na lang, nasulat ko as a remark kasi I was not able to write it. ang determinant ng type 1 ay negative 1, di ba?

**[30:45]** Kasi kapag ang determinant ng identity ay what? 1. Pag nagpalit ka ng dalawang rows, nagiging negative 1. Ang determinant naman ng type 2 elementary matrix ay alpha. And of course, alpha is not 0, right? Yung scalar na yan, hindi pa pwedeng 0. Okay? At ang determinant ng EIJ alpha, ito yung type 3, from 1, 1 pa rin naman ang determinant. Now what I'd like to say, what I'd like you to observe is that in any case, ang determinant ng elementary matrix ay hindi zero.

**[31:25]** Never magsi zero. Kaya nga, napatunayan natin that if E is an elementary matrix, its determinant is not zero. Tandaan yan ha? Pag elementary matrix ang matrix, ang determinant niya is never 0. Kasi ang determinant niya kundi negative 1, 1, or alpha. Eh ang alpha naman natin ay hindi pwedeng 0. Remember? Did you remember? Hindi pa pwedeng 0. So, in general, we can say that if E is an elementary matrix, ang determinant niya ay hindi 0. Now, paano na ngayon kapag si A ay non-singular?

**[32:06]** Ganito guys. Naaalala niyo yung unifying theorem natin? Sabi natin, if A is non-singular, we were able to prove last time that if A is non-singular, it is in fact a product of elementary matrices, meaning you say, you can decompose it into factors wherein each factor is an elementary matrix, lahat ito elementary matrix, okay? So pag kinuha ko yung determinant ng A, I have to get the determinant of all these elementary matrices. Now, isipin nyo guys, itong malaking tipak na ito, yung mula E2 hanggang EK, isipin nyo si B yan.

**[32:50]** Pag inisig mong B yan, ia-apply mo ito, meron kang determinant ng E times B. So, pag in-apply mo yung box na formula, magiging, ah, not right away, let me show you ha, what will happen. Mahihiwala yung determinant ng E1 sa determinant ng B.

**[33:13]** But then again guys, itong matilang determinant, pwede mong isipin ulit ito na E times B, right? So, if you apply the box formula one more time, you will keep on writing the determinant this way. Ang may iwanan naman ay determinant ng E3 hanggang EK, right? And if you continue doing the process or continue, yeah, applying the process, Eventually, yung determinant na yan ay magiging ganito guys. And using the fact that elementary matrices have non-zero determinants, if this thing is non-zero, this thing is non-zero, this thing is non-zero, what is their product? their product is therefore non-zero.

**[34:08]** Nakuha niya? Kaya kapag si A ay non-singular, na-prove na natin na ang determinant niya ay hindi zero.

**[34:19]** Okay? Kaya lang guys, that is just 50% of the theorem. Kasi remember, tingnan nyo ha! Balikan natin yung theorem natin. The main theorem says that a square matrix is non-singular if and only if the determinant of A is not zero. Ang napakita pa lang natin kapag si A ay non-singular, because it's a product of elementary matrices, basically yun yung reason, no? Then its determinant is not zero. Yun yung napakita natin. Eh what about the other case? Yung bakit kapag, eh paano naman pag-singular si A?

**[35:01]** Zero ba ang determinant? Dapat. So, yun yung kailangan natin ipakita further. Saan ba ako natapos? Dito tayo natapos, okay? Ito na yung pabaligtad. Paano naman kapag si A ay singular? So, dapat mapakita naman natin ang determinant dapat ng A0, na? O ganito. Para malaman mo kung ano yung determinant ng A, kunin mo yung RREF. Yung RREF ni A na singular, tawagin mong B. And of course, dahil si A ay singular, yung RREF na yan, hindi siya identity matrix.

**[35:45]** At pag hindi identity matrix ang RREF, automatic magkakaroon ka ng 0 row kasi magkakaroon ka ng fewer than N na 5 votes meaning yung rank mo will be less than N. Agree? So ang determinant nung RREF na yun should be zero. Do you agree? Kasi may zero siya, so ang determinant niya has to be zero. But you know guys, si A ay row equivalent kay B. Meaning to say, maa-obtain mo si B kay A by applying elementary row operations.

**[36:27]** E sa bawat elementary row operation, it corresponds to one elementary matrix, a multiplication of one elementary matrix on the left. Kaya pwede niyong isulat si B in the following form, okay? Tapos sa kaliwa niya may mga maraming elementary matrices. Each one correspond to an elementary row operation that you performed, okay? So if I take the determinant of both sides, the determinant ng kaliwa is zero. Okay? Tapos, once again, if you apply the same argument as above, yung determinant neto magiging ganito.

**[37:08]** Agree? Na? Ina-apply ko lang din nung paulit-ulit yung property na ito. Now, guys... None of this determinant is zero. So that product is never zero. Kung zero yung product netong dalawa, sino ang zero? Aha! Kung non-zero ito, pero yung product na buo ay zero, dapat ang zero yung determinant. ng A sa ulit. Pag si A ay non-singular, ang determinant ay hindi 0. Pag si A ay singular, ang determinant ay 0.

**[37:51]** So anong natutuhan natin? A is non-singular, if and only if the determinant is non-zero. Therefore, establishing the main theorem.

**[38:08]** Nakita nyo guys how our results work all together to prove this main theorem?

**[38:19]** Naunawaan ninyo, bakit ang determinant ay determiner? Medyo sabi ko nga, it took us a very long time to be at this point. I mean, hindi ito simpleng theorem lang kasi, you know, andami nating concepts na ginamit from previous lesson, to be able to establish that. And you know guys, with that, this part will be ended by adding one more statement to the unifying theorem. yung first five was already established, yung equivalence nung unang lima was already established last meeting. Ngayong, ngayong araw, napakita natin yung equivalence nung one at six, so therefore, six can be added to the list of equivalent statement.

**[39:11]** So, dapat kung non-singular si A, one way to look at it is true determinants, dapat ang determinant ay hindi zero. So, we are now 6 over 20 of the way para matapos yung semester. Diba sabi ko 20 statements to at the end? So, we are 6 over 20 of the way. Lapin na tayong mga lahat eh. Now, in reality guys, sa totoo lang, yung boxed property kanina na ang determinant ng eb ay determinant ng e times the determinant of b. The truth is, this property holds kahit na hindi naman elementary matrix yung E.

**[39:57]** In other words, the determinant is a multiplicative function. Bakit? Anong instrument ng multiplicative function? Pag kumukuha ka ng determinant ng product, It is the product of the determinants of the individual pieces. Regardless kung si A man ay elementary or not. Totoo pala siya na. So maybe I can show you the proof kasi it's not really hard to imagine. So, the idea of the proof is very similar to what we had before. Ang gagawin lang natin, dalawang cases. Unang case, pag si A ay non-singular, pangalawang case, pag si A ay singular. Hatiin ko yung dalawang, did you understand?

**[40:41]** Okay, case one. If A is non-singular, then by the unifying theorem, it can be decomposed as a product of elementary matrices as shown. So yung determinant ng AB ngayon is the determinant of all of this applying the previous arguments that we had. nakahati-hati siya into this, right? Now, burahin nyo sa isipan nyo ito, titigan nyo lang ito, di ba pwede mo ulit pagsamasamahin to, what I'm trying to say is, magiging ganito, from the last two, yung last two pwede mong isulat ng ek minus 1 ek. Eventually, Kaya mong pagdikit-dikitin ulit yung mga e na yan, all together, parang reversal lang nung nangyari, pero nakahiwalay na yung that b.

**[41:31]** But you know, saan equal to? Yun lang si a. So ang nangyari, ang determinant ng a, b ay determinant ng a times the determinant of b. finish ka na dito sa case na to. You know, saan yung medyo mahirap na part? Ang mahirap na portion dito kapag si A ay singular kasi. Wala kasi tayo masyadong masabi, no? I mean, pag singular si A, hindi siya product ng elementary matrices. So what? So ganito. Assume that A is singular. Ipapakita muna natin that the product AB has to be singular as well.

**[42:12]** Kasi alam nyo bakit kapag pinakita ko ito tapos na tayo? Kasi kung si AB ay singular, according to the main theorem, yung left-hand side neto zero. Kung si A ay singular, zero ito. Ngayon kung anuman yung lecheng ito, it doesn't matter. The equation will be true regardless.

**[42:36]** Did you understand the logic? Bakit ito na lang yung ating ipapakita? We just claimed that We just wanted to prove that the product AB has to be singular, kasi if that time comes na singular ito talaga, zero na itong left-hand side. Itong determinant ng A0, kung ano man yung value nung letching determinant of B na yan, we don't care. Kasi, regardless, the equation is already true. Okay? So, pag napakita natin na si AB ay singular, tapos na tayo. Okay? Paano ba natin ipapakita ni si AB ay singular? Ano ba yung mga alam natin tungkol sa mga non-singular?

**[43:16]** Ito guys, may gagamitin ako sa unifying theorem na I have to review kasi baka hindi nyo natandaan. In particular itong portion na ito ng unifying theorem about homogenous linear system. Tandaan ninyo guys, Pag si A ay non-singular, no? Lahat ng homogenous linear system nyo na Ax equals 0, isa lang ang solution. Yung zero solution lang, yung trivial solution. So kung if false natin ito, pag si A ay singular ngayon, Kapag si A ay singular ngayon, ibig sabihin, this has other solutions than the zero solution. Meaning to say, AX equals zero has a non-trivial solution. Anong meaning nung has a non-trivial solution?

**[44:16]** Ibig sabihin nyan, merong vector y na hindi naman zero, pero it solves the linear system. Pag nilagay mo siya dun, ay is equal to zero, pero hindi siya zero vector. Did you understand the equivalences and why I was able to conclude this. Sige, pabalik tayo dun saan na ha? Pabalik tayo dun sa proof. So again, pag napakita ko na si A, B ay singular, tapos na. Now ganito, ang bida dito guys, yung homogenous linear system na A, B, X equals 0. ipapakita ko, guys, na yung homogenous linear system na ito ay may non-trivial solution.

**[45:08]** Pag kasi napakita kong may non-trivial solution to, ibig sabihin, hindi dapat non-singular si AB, dapat singular siya. ang tanong, saan kamay ng Diyos natin kukunin yung vector Y na yon? Na non-trivial. So ganito po, okay? First of all, dahil si B is assumed to be singular, ah, hindi to assumption. Ah, if, hypothetical pala ito. Yung case 2 pala guys, magkakaroon ng mga sub-cases. Oh my good lord. So ano nga yung case 2 natin? A is singular.

**[45:52]** Ahatiin ko ito sa dalawang sub-cases pa. yung subcase 2.1, ito yung si B naman yung titignan natin, singular, yung other cases of course, B is non-singular. Anong magiging conclusion in either cases? Let's see, okay? Doon muna tayo sa B is singular. Kung si B ay singular, gaya ng sabi ng unifying theorem, dapat yung bx equal 0 may non-trivial solution. Sa makatwid, merong non-zero vector x so that bx is equal to 0. Okay? With that in mind, Pag minultiply ko ngayon yung AB, doon sa same vector X, you will get A times BX by associative property, tapos yung BX nagiging 0, tapos ang A times 0 is 0.

**[46:46]** So technically, yung non-zero vector X na yun is also a non-trivial solution. to ABX equals 0. So therefore, AB has to be singular. Kung titignan nyo yung three diagram natin, A is singular, B is singular, B is non-singular. Yung case na ito, in-imply na na si AB is singular. Nakuha niya? Eh, how about when B is non-singular? No? Yun yung sa subcase 2.2. Pag si B naman ay non-singular, guys, eh di ba si A ang singular?

**[47:32]** By assumption, di ba? Yun yung unang root nung three diagram natin sa a is assumed to be singular. So you can use that fact. Because a is singular, meron ng non-zero vector na y so that ay is equal to zero. may non-trivial solution doon sa ax equals 0, right? Tapos, anong gagawin natin? Ididefine ko yung vector x as b inverse times y. Kasi nga si b ay non-singular, may inversi b. Paano ko naman naisip to? Secret, kasi bright ako eh. Charot. You know guys, ano bang gusto ko sabihin dito?

**[48:15]** This vector x has to be non-zero. Alam nyo bakit non-zero dapat si x? Kasi kung zero siya, ano mangyayari? Kung zero kasi yan, nagkaroon ng non-trivial solution yung B inverse, eh yung B inverse nonsingular din eh. So dapat yung x dito cannot be 0. Right? Pag 0 kasi ito, magkakaroon ng non-trivial solution yung B inverse x equals 0. So, it will follow that B inverse will be singular. Hindi pa pwede yun. B is non-singular. So, yung inverse din yan, non-singular. So, dapat yung vector x na yan ay hindi zero.

**[49:00]** Ang maganda ngayon guys, tiga nyo ha, pag minotip, minotip like yung a, b sa x, by associative property a times bx, saan equal yung bx? Kung ito yung x, magiging a y equals 0. Bakit? Kasi may iniski pa kong portion dito eh. Yung bx ko kasi ay a times b, b inverse y. nakuha niyo yun. Si x kasi ay b inverse y, so nireplace ko yung x by b inverse y. E ang b, b inverse magka-cancel, identity yan, kaya may iiwanan dito ay.

**[49:43]** But what is ay equal to? It is equal to 0. So ano yung x na yun na non-zero? It's a non-trivial solution to the linear, homogenous linear system AB x equals 0. In this case, singular pa rin yung AB kasi may non-trivial solution yung AB x equals 0. And if you look at the tree diagram, ang naging conclusion din dito, AB is singular. So meaning to say, in either case, laging ang conclusion ay AB is singular and according to our claim, we are done.

**[50:28]** Nakita nyo, no? Kaya... Ito yung mahirap na portion nung pagiging math major, you know, when we try to write proofs, parang abogado na nag-a-argue, right? Nakikita nyo ba yung similarity nya kapag ikaw ay isang abogado na nag-a-argue to prove something? yun nga lang, kapag lawyer ka na, as in lawyer sa court, true evidence ang ating ano, ang ginagamit na dito sa mat, puro facts, no? Gets? Agets ninyo? And therefore, we are done.

**[51:14]** Why are we done? Kasi si AB, napatunay na natin singular, so that's it. That's the end of the proof. And you know guys, nage-extend yung multiplicative property na yun sa kahit na ilang product. Let's say marami kang square matrices na n by n, you can distribute the determinant in this way.

**[51:42]** Okay? May tanong si sir. Question. Ang determinant ba ng A plus B pareho sa determinant ng A plus determinant of B? What do you think? What you think? What you think? Of course, no. Alam nyo, kasi kung yes ang sagot dyan, nilagay ko na as a theorem. Tsaka, masyado ng maganda ang mundo kapag nangyari yan. I mean, we're not really living in a perfect world, so... hindi ito mangyayari. Masyadong ano, masaya ka naman masyado, pati undeterminate ng sum-sum non-determinants. Naintindihan nyo?

**[52:29]** Undeterminate ay multiplicative pero hindi po additive. Madaling lang gumawa ng counter example. Halimbawa, A. Ha? Anong gusto nyong A? Kunwari, itong A na ito, negative 1, 0, 0, negative 1.

**[52:55]** Yan, okay? Ang B kunwari, 1, 0, 0, negative 1. So ang A plus B mo ngayon ay zero matrix, correct? ang determinant ng A plus B ay 0, of course. Ang determinant ng A ay negative 1. Ang determinant naman ng B, negative 1 din. Ang determinant ba ng, ang negative 1 plus negative 1 ba, 0? Hindi, di ba?

**[53:31]** Gets ninyo? This is a very good, it's an easy counter example. You can create more counter examples if you wish, no? But generally, the determinant of the sum is not equal to the sum of the determinants. Huwag kayong magpapalin lang. Ang totoo, ang determinant ng product kahit na ilan yan ay product ng mga determinants, okay? Isa pang magandang result. Guys, this is very nice. Alam nyo kapag si A ay non-singular, ang determinant ng A inverse, ay reciprocal ng determinant ni A.

**[54:16]** Nice, no? Halimbawa, meron kang matrix. Ang determinant, for example, ng A, ay let's say 2. Dahil si 2 ay hindi 0, therefore A is non-singular, correct? So may inverse siya. Now, without Do you remember how complicated it is to get the inverse of A? It's really a lot of work, right? But you know guys, if you are just interested about the determinant of A inverse, you don't really need to get A inverse. Kasi the truth is, pag alam mo na yung determinant ng A, alam mo na yung determinant ng A inverse. And the determinant is just the reciprocal. The determinant will be one half.

**[55:02]** Isn't it a nice property? Na? Kailangan mo bang kumpitin yung inverse para malaman yung determinant niya? Hindi na po. alam mo na siya kagad in advance or ine-expect nyo na. Okay?

**[55:22]** Okay, okay, okay? Sige ha? Bakit po ito totoo? Ang sagot nang galing sa equation na ito. Kasi alam natin ang A times A inverse ay identity guys. Right? All you have to do is to get the determinant of both sides. Should you do this, because of the multiplicative property, the left-hand side decomposes into the product determinant of A times determinant of A inverse. And then the determinant of the identity because it is 1, okay? Now, this is a non-zero number guys.

**[56:06]** Scalar na lang yan. So should you be interested with this, how do you write it in terms of the determinant of A? It follows that the determinant of A inverse has to be 1 over the determinant of A. Nakuha nyo? It's not really hard to prove, okay? Yay! Na-prove na natin yung ating corollary. And we are now down to the last portion of this lesson, which is an alternative method, kasi diba ang method na inalakay natin yung reduction to upper triangular using elementary row operation, na? Now, etong tinatawag natin cofactor expansion or minsan tinatawag na Laplace expansion.

**[57:00]** It's named after this French mathematician, Laplace. Hindi siya Laplace ha.

**[57:09]** It's also called as the Laplace expansion but I'd like to just call it the cofactor expansion. It's basically a method to compute a determinant. I'm not saying this is better, there are times that it is better, but there are times that it is not as good as the reduction to upper triangular. Pero alam nyo kung ano yung best? Ang best ay kung kaya nyong pagsabayin yung dalawang method na to in appropriate times and setting. Ituturo ko sa inyo kung papaano yun, no? Kumbaga, ang sinasabi ko, huwag kayong reduction kung reduction lang through elementary row operations or cofactor expansion lang hanggang mamatay kayo.

**[58:00]** Ang pinaka-optimal ay gamitin yung isawin, it is advantageous. Ang tanong, paano mo malalaman kung advantages gamitin yung reduction to upper triangular? At kailan advantages yung cofactor? Ako ginagamit ko siya ng sabay. And I will teach you that in the following slides. Huwag kayo mag-alala. Pagsisimula muna tayo, ano bang ibig sabihin ng cofactor? Sige? Balikan muna natin yung ating 3x3 determinant. For you, for, just, ah, para lang makuha ninyo anong ibig sabihin ng cofactor at bakit siya tinawag na cofactor. Ito po yung 3x3 determinant natin, yung 6 na terms na nakikita ninyo, ito yung 6 na arrows. tatlong pababa, tatlong pataas.

**[58:50]** Yung mga positive ang pababa, yung mga negative yung paakyat, okay? Kung mapapansin ninyo, if you look at the first row, titigan nyo yung first row, if you look at the first row, di ba remember by the definition, Pukuha ka ng tigitigisa sa bawat row, correct? So in short, in the first row, laging magsisimula ka sa first row, regardless. So dahil tatlo yung entry sa first row, pwedeng magsisimula ka sa A11, pwedeng magsisimula ka sa A12.

**[59:30]** Or pwedeng magsisimula ka sa A13. Kaya ngayon determinant nyo guys, pwede mong hatiin, i-classify into three parts. Aning tatlong parts? yung mga terms na magsisimula sa A11, or terms with A11 as a factor, plus yung mga terms na magsisimula naman sa A12, plus yung mga terms na magsisimula sa A13. Do you understand what I'm trying to say guys? Hello? Did you understand? Okay, so let me highlight it for you. For example, itong mga terms na nagsisimula sa A11, eto siya o, dalawa siya, okay? Yung mga terms naman nagsisimula sa A12, eto naman siyang dalawa.

**[1:00:18]** At yung mga terms na nagsisimula sa A13, eto naman yun. Ay, let me color it. using blue. I hope that you can understand what I'm trying to say, maigugrupo mo siya into 6 parts. And you know guys, you know guys, dahil tingnan nyo yung mga red terms, dahil common yung A11 sa kanila, pwede mong i-factor yung A11. ay ito pala, yung pinagsama-sama ko pala, may pa drawing-drawing pa ako, pasensya na ka hindi ko kabisado kasi yung slides ko, yan. Ito yung mga terms na may A11, ipafactor ko ngayon yung A11, okay?

**[1:01:04]** Tapos, Ito naman yung mga terms na may A12, so dahil common nga yung A12, so factoring ko yung A12. At ito naman yung mga terms na may A13, so factoring ko yung A13. And you know guys, ano yung mga matitira na to? Ano yung mga natira? They are actually the cofactors na tinatawag. So yung kung ano man yung factor na yun, that is what we call as the cofactor of the N3A11. Ito naman yung cofactor nung N3A12 at ito naman yung cofactor nung N3. A13. So the idea guys is, lahat ng entries ng matrix may kanya-kanyang mga cofactors.

**[1:01:48]** The question is, how do we think about the cofactors? And let's say, ano yung cofactor nung A21? Ang gagawin mo naman, titignan mo yung second row. Ang mga terms, i-classify mo into 3. Yung mga terms na dumadaan sa A21, yung mga terms na dumadaan sa A22, at yung mga terms na dumadaan sa A23. Kung gusto mo yung cofactor ng A21, collect tayo mo yung mga terms na dumadaan sa A21, tapos i-factor mo yung A21, yung matitira. yun yung kanyang cofactor.

**[1:02:24]** Did you understand kung anong ibig sabihin natin ng cofactor through this mini example? Okay, so let's try to generalize it. In general, the cofactor of the entry AIJ as an entry of the matrix A is basically the scalar AIJ, tapos may C, notation ko yun to indicate that it is the cofactor of capital AIJ. Siya yung other factor, no? Kasi pag ito yung mga terms, yung determinant ng A, mahati mo into two parts.

**[1:03:07]** yung mga terms with AIJ plus yung mga terms na walang AIJ, yung hindi dadaan sa AIJ, okay? Of course, of the terms that contains AIJ, you can factor the AIJ out. Ang maiiwanan dito, yung cofactor nung AIJ. Did you understand the equation? In English ko na lang yung equation para mas understandable for you. Did you understand? Ito yung dinidenote natin by AIJ na may C sa ibabaw.

**[1:03:50]** Now, kindly take note, yung lecture notes na ina-upload ko, iba yung notation na ginagamit doon kasi it's a very, it's an old lecture notes, no? Iba na yung notation na ginagamit ko, please bear in mind. I believe kasi itong notation na ito is a little better than than that, okay? I have a reason why I have to adapt a different set of notations for cofactors. Pasa cofactor may letter C sa ibabaw, okay? So the question is guys,

**[1:04:28]** before we talk about, before I ask that question, ang natutuhan pala natin ay ang sumusunod, at yung tinatawag natin cofactor expansion, okay? Ang sinasabi neto, okay, meron kang square matrix, for each i starting from 1 to n, the following equation holds. So, anong ibig sabihin yan? Guys, eto, ang sinasabi neto, pwede kang pumili ng kahit na anong row, okay? Pag nag-fix ka ng kahit na anong row, row i, kunwari ito yung matrix ninyo, tinignan nyo yung row i, ai1, ai2, ain.

**[1:05:15]** Pag ikaw ay magkocompute ng determinant, by definition, kukuha at kukuha ka ng entry from this row. Hindi mo pa pwedeng laktawan yung row na yan. Lahat ng row makukuhanan mo. Kaya nga yung mga terms ng determinant, yung determinant ninyo, maahati nyo into parts, di ba? ang determinant mo ay yung mga terms na dadaan sa AI1, yung mga terms na dadaan sa AI2, and so on, yung mga terms na dadaan sa AIN. So, tapos, i-factor mo yung AI1, ang may iwanan dito yung cofactor ni AI1.

**[1:05:56]** Nakuha nyo? So, basically, this notation is simply a re-expression of this equation. Pareho lang sila. Right? Ang tawag natin dito ay cofactor expansion along row i. Kasi, namili ka ng isang row. Naalala nyo, sabi ko dun sa duality principle, lahat ng mga theorems natin about rows can also be said with columns. The truth is, pwede ka rin mag-fix ng isang column. I-consider mo yung transpose kasi ni A, magiging row yan. Okay? So if you have selected column J instead, ito yung mga terms na merong A1J. Ito yung mga terms na merong A2J as a factor, at ito naman yung mga terms that has ANJ as a factor.

**[1:06:54]** Now you know guys, may anay note. So the question is, how does one compute? The cofactor. Kasi alam nyo, sa totoo lang, hindi madaling mahanap yung cofactor na yan. Alam mo namang ilista ko lahat ng mga terms, ipunin ko, tapos i-factor ko para makuha yung cofactor. Naintindihan nyo yung complication sa pagkakalculate na itong cofactor na ito? Hindi siya po madali kung iisipin mo meron bang formula para makompute natin yung cofactor nyan so I can use this formula instead fortunately there is okay but before that bakit ba big deal itong cofactor expansion kasi guys, ito ay advantages gamitin pag may isang row or isang column ka na maraming zeros.

**[1:07:55]** Kasi guys, pag may isang row, let's say, sa row ay maraming zero, yung mga terms nito kung maraming zero ay halos mauubos. Do you agree? Do you agree na halos mauubos yan pag ano, pag, ah,

**[1:08:18]** so one thing remains or one question remains in, ah, one question remains in to be answered. Ang tanong, paano ba natin makocompute itong mga cofactors na to para maka-under na yung trend? Kasi, ah, ito na yung formula. Kaya lang, ito, obviously, nasa matrix lang ito. Kaya lang ito, hindi mo siya right away makikita sa matrix, no? Paano ba sila kinocompute yung mga cofactors na yan? Fortunately, meron tayong formula sa kanila. Ito yung cofactor formula. Oh my good lord! So let me explain what is this cofactor formula. So ganito guys.

**[1:09:03]** Okay ha? Makinig mabuti, makinig mabuti, makinig mabuti. Ito yung matrix A ko, okay? Ito yung row i, and ito yung AIJ, AIN. Ito yung column J, A1J, AIJ, ANJ. Do you recognize your matrix? Ang bida dito, hinahanap natin yung cofactor ng AIJ. Pag sinabing cofactor ng AIJ, well, yung AIJ times AIJ cofactor, this is the sum of the terms with AIJ in it. Sa makatwid, kung iisipin mo siya pictorially, ang laman na ito, lahat ng mga terms na dumadaan sa AIJ.

**[1:10:01]** Hindi mo kukunin ito, hindi mo rin kukunin ito, right? Siyempre, determinant ito dahil permutations yan, hindi ka pa pwedeng kumuha dito, hindi ka rin pa pwedeng kumuha dito. They get the idea? Yung ibang factors, kukunin mo dito sa paligid. Bawal dito sa same row, bawal dito sa same column. Kaya alam nyo kung paano kinocompute ito? Yung cofactor niya? i-delete mo itong row na ito, i-delete mo itong column na ito. Kung ano yung may iwanan, kukunin mo lang yung determinant nun. Kaya lang may catch. May extra factor na negative 1 raised to i plus j.

**[1:10:44]** Paano ba yun? Bakit may ganyan? Let me explain that. mamaya, okay? Magfocus muna kayo. Tandaan nyo yung cofactor of Aij can be obtained as getting the determinant of the same matrix, didelete mo lang yung row i tsaka column j. Kaya nakita nyo yung size nya is one dimension less. kasi dinilit mo yung isang row, dinilit mo yung isang column. Kukunin mo yung determinant nun. Yun yung nari dito. Ngayon, yung determinant na yun, papalitan mo yung sign niya or hindi, depende kung anong position niya dito sa matrix. Ayan o. Kung yung i plus j ay even, hindi mo na papalitan yung sign. Pero kapag ang i plus j naging odd, papalitan mo yung sign.

**[1:11:44]** Bakit may pagpapalit ng sign? Kasi guys, yung proof na ito, yung proof ng formula na to, actually, ah, ang gagawin dyan, yung Alam nyo kung anong kasaysayan na ito, ganito ha? Anong papapaliwanag to sa pinakamadaling paraan. Okay, so let me try my best guys. Let me just try my best. Ito si A. Ito yung column 1, column 2, column J. column N. Kinati ko yung matrix into columns, ha?

**[1:12:22]** Ang gagawin ni sir, makikipagpalit, makikipag-column interchange ako, hindi nga niya, makikipag-column interchange ako sa katabi niyang column, so E, J, J minus 1, pero lalagyan ko ng C, ibig sabihin, I'm working on columns. So, pag ginawa ko yan, magpapalitan yung dalawang columns, right? Susundan ko ng, pag nandito na siya, magpapalitin ko naman si EJ minus 2, EJ minus 1. In short, Pag nakarating na siya dito, makikipagpalit ulit ako sa katabi niya.

**[1:13:03]** In short, isa-isa akong nakikipagpalit sa katabi niya hanggang mailagay ko, ang goal ko kasi, ang end goal ko, mailipat ko si CJ dito nang hindi ginugulo yung order nung iba.

**[1:13:25]** Nakuha niyo?

**[1:13:30]** Bakit isa-isa? Kasi you may wonder, bakit sir, isa-isa kang nakikipagpalit? Kasi kapag kuha tayo ng scratch. Anwari, 1, 2, 3, 4, 5. Let's say si 3, gusto kong ilagay dito sa unahan. Pwede nyo sabihin sa akin, edi sir, makipagpalit ka na lang kay 1. Pag ginawa ko kasi yun, guys, makikita nyo, yung order nung 2, 3, 4, 5, ay yung order nung 2, 1, 4, 5, hindi maganda. Nagulo. Whereas, kapag ang pakikipagpalit mo ay isa-isa, pag isa-isa ka nakipagpalit kasi, let's say, magpapalit muna si 2 at si 3.

**[1:14:09]** maging 1, 3, 2, 4, 5. Pag nandito na ngayon si 2, at tama ba yung ginawa ko? At pag nandito na ngayon si 3, dito ka naman makikipagpalit, magiging 3, 1, 2, 4, 5. Yung natural order ng ibang elements, hindi ko ginagalaw. So I prefer interchanging one column at a time. Kasi hindi ko dinidisarrange yung other parts of the matrix. Okay?

**[1:14:47]** Okay. May tanong si sir, nakailang column interchange ako para mailipat ko si 3 hanggang sa unahan? Diba naka? dalawa tayo. Tandaan nyo yung number na yan na nakadalawa. Eh dito, makakailang column interchange ako para mailipat ko yung column J sa unang column.

**[1:15:12]** Kung column J siya, ilang column interchange yung gagawin ko para makarating siya sa unang-unang position. What's the total number guys? Kapag nasa column 3 ka, kailangan mo dalawa. Kapag nasa column J ka, ilan ang kailangan mo? What's the formula?

**[1:15:34]** Very good. J minus 1 column interchanges. Very good. Okay. J minus 1. Okay na! Nandito na ngayon yung column J. By that time, nandito na yung Aij. Diba? Hindi pa ako tapos. Kala niyo, tapos na na. Yung mga rows naman ang titignan ko. Ang goal ko naman, maiyakyat siya dun sa tuktok.

**[1:15:58]** Pag naiyakyat ko siya sa tuktok, ilang row interchanges yun? All in all, I minus 1. Kagaya ng J-1 ninyo, yun nga lang, binibilang mo from i. Ang tanong, upon doing that, ilang beses nagpalit yung sign ng determinant? Diba bawat row at column interchange, nagpapalit yung sign? So, all in all, naka i-1 plus j-1 interchanges ako ng sign. Nakuha niya? Yap. Pag sinimplify nyo ito guys, magiging ano to eh, negative 1 raised to i plus j minus 2.

**[1:16:43]** Eh yung minus 2 kasi na yun, even yun. So pag... pag ano, pag hiniwalay ko siyang ganyan, 1 pa rin ito, so it just simplifies into negative 1 raised to i plus j. Now, yun yung kasaysayan nun, ba't may ganon sa formula? Kasi ang gusto ko, ilipat itong column na ito dito, tapos yung row na ito doon sa ibabaw. para nasa 1-1 position siya. Kasi pag nasa 1-1 position ka, yung cofactor nung nandyan, i-delete mo lang ito. Ang may iwanan, yung MIJ pa rin.

**[1:17:23]** Did you understand? yung, yung factor na to accounts for the number of times na nakipag-column at row interchange ka. Para mailipat yung AIJ sa 1-1 position. Okay? Nakuha niya? yun yung kasaysayan ng formula na, yun yung pinakamadaling paliwanag na pipwede kong ibigay sa inyo. You can read about the full proof doon sa ating lecture notes. It's basically there. Okay, let's now apply this in action. Okay, ito live na natin gagawin. yung cofactor expansion.

**[1:18:05]** So, we will evaluate the following determinants, guys, one by one. Mag-start tayo dito. Now, anong turo ko sa inyo? Ang turo ko sa inyo, piliin mo yung row or yung column na may pinakamaraming zeros. Tama ba? Hello? Is that correct? Pipiliin mo yung row or column na may pinakamaraming zero. Sa case na to, sinong row yun? Or column? I think this is row number two, no? Tama? If you just apply the row cofactor expansion, Magiging ganito siya, guys.

**[1:18:52]** Okay, lilista mo yung mga row entries mo. 2, 0, 1, 0. May mga katabi yan, yung mga kanilang mga cofactors. Now, do you think these terms will matter? Hindi na, kasi regardless kung ano yung cofactor nila, the term remains 0. Kaya ang katotohanan, ilang terms na lang ang mabubuhay? Dalawa na lang. So ang tanong, anong cofactor nung entry na 2 na yan? Ang formula natin guys ay negative 1, raise 2.

**[1:19:35]** Aalamin mo anong position niya? 2, 1. Kaya sa taas na ito, maglalagay ka ng 2 plus 1. Okay? Second row, first column. Tapos, dideletin mo yung second row, first column. Kukunin mo na lang yung determinant ng negative 1, 3, 5, 1, 3, 4, 3, negative 2, 8.

**[1:20:03]** Nakuha nyo guys! O ulit! Just to clarify, no? Dinilet ko ito para maiwanan yung 3 by 3 na matrix na yan. Ang tanong, ano naman po yung cofactor nung 1? Ganon pa rin yung formula. Negative 1, raise 2. Anong position ba nung 1? 2, 3. So, maglalagay ka dito ng 2 plus 3. Buburahin mo ngayon yung second row third column sa isipan ninyo ang maiwanan 2, negative 1, 5 6, 1, 4 negative 7, 3, 8 Nakuha nyo?

**[1:20:54]** Ha? So, yung alternating na negative 1, it's actually negative in this case, no? Kasi, odd yan eh. Okay? Di ba, odd siya? Ito rin, odd. Kaya ito ay kanyan. So, before we actually compute guys. Ano napansin ninyo sa method na ito? Yung method na ito guys, it reduces your 4 by 4 determinant into sums of 3 by 3 determinant. And guys, you can keep going. Meaning to say, Kung gusto mo, mag-cofactor expansion ka sa mga 3x3 para magkaroon ka ng 2x2.

**[1:21:42]** Did you understand? At baka kapag 2x2, mag-cofactor expansion ka pa, hambalusin kita, no? Kapag 2x2, apply nyo na kagad yung crisscross method. Yan talaga yung goal. Ang goal ng cofactor expansion... is to reduce your very big determinant into sums of small determinants. Kasi yung small determinants, meron tayong formula. Okay? Now, question. Do you want to take this one notch higher? I mean... Gusto nyo pa bang padaliin yung ating buhay? Kasi ayoko mag-compute ng dalawang 3x3 na yan. Tignan nyo muna itsura, nakakamata yung itsura nya, no?

**[1:22:27]** Okay, bibigyan ko kayo ng another way para mapadali yung buhay nyo lalo. So again, ang in-apply ko dito ay cofactor expansion along the second row,

**[1:22:42]** okay? Ako, ganito, ako, si sir, ganito ko siya personally gagawin. I will not, I will not do row expansion ng

**[1:22:59]** kaagad. Oo, correct kayo, napansin ko na sa second row, sa second row, dalawa lang yung non-zero entry, kaya mag-i-insum yan ng dalawang 3x3. Diba? Tama kayo doon. Pero you know, nakakita ko ng 1 dyan sa second row eh. Kaya ko kasing gamitin yung 1 na yan. to eliminate the two on the first column. Diba? Pag nagawa ko kasi yun, isang 3x3 na lang. Hindi naman mahirap mag-eliminate eh. Do you guys understand? Ito yung sinasabi ni sir, yung mixed method, no?

**[1:23:42]** Pero pwede nyong gamitin yung elimination technique. along with cofactor expansion to make your life easier. Ako personally, I prefer this over yung plane na cofactor expansion kasi kita nyo naman yung pagdadaanan yung determinant dun sa daas na makabagbag damdamin ang itsura niyan. Itsura pa lang nung 6 tsaka nung 8 dyan, may negative 7 pahayop. Diba? I mean, come on. Huwag nyo pahirapan yung sarili nyo. Do it smartly. Ay, may salita ba smart? Do it smart.

**[1:24:21]** I mean, you can do it kung matsaga kayo. Diba? Kung matsaga kayo, pwede nyo lang gawin yung taas. Kaya lang, hindi kasi lahat ng tao ay kasing tsaga nyo. No, ayun, katulad ko, hindi ako matsaga sa ganitong mga bagay. So ginagawan ko talaga ng paraan yan to make it easier for my processor. Kasi yung processor ko hindi masyadong mabilis. Especially to arithmetic. like this. So, how do I eliminate the 2 gamit yung pivot na 1? Well, I can do a type 3 column operation, nasa first column yung buburahin, yung pivot nasa third column, ang ating factor ay negative 2.

**[1:25:05]** naintindihan nyo yung notation ni sir? You understand my notation? Column operation tayo, ha? So, paano ang multiplication? Paganan guys, ha? Paganito po, ha? Ah, paano ba?

**[1:25:23]** Ay! Teka, nahilo ako. Nahilo ako. Anong nagawin? I-multiply yung... negative 2, tapag ganun.

**[1:25:38]** Nakuha niya, ganun yung arrows natin. Imultiply yung negative 2 sa third column, ia-add sa column 1. So ganito, negative 2 times 3, that's negative 6, plus 2, negative 4. Ito, it will be 0 kasi that's the intention. Agree? Okay. Negative 2 times 3, negative 6 plus 6. Kita nyo, nag-zero na rin to. Nahawa na siya, no? negative 2, times negative 2, negative 4, ah positive 4, minus 7, negative 3.

**[1:26:28]** Gets nyo ba? Gets nyo ba? Now, it is fun and easy kasi yung second row ninyo, isa na lang yung nabubuhay na term tapos 1 pa yan. Diba? So, by using cofactor expansion along the second row, it now reduces to a single 3x3, 1 times. Ano bang position ng 1? Anong position ng 1? 2, 3, kaya 2 plus 3. Tapos buburay mo yung 2nd row 3rd column, it will be negative 4, negative 1, 5, 0, 1, 4, negative 3, 3, 8.

**[1:27:17]** Gets nyo ba?

**[1:27:23]** Dahil may angking katamaran ka talaga, ayaw mong pumayag na magte 3x3 determinant ka, di gawin mo lang gawin yung gusto mo. For example ako, gagamitin ko yung 1 na yan para patayin yung 4. Every time na nakakakita ko ng 0, I take that as an opportunity tsaka ng 1. Every time na makakakita ka ng 1, you can take that as an opportunity. Eh paano sir, pag walang 1, pwede kang gumawa ng 1, mag-factor ka in a row or in a column, okay? Naintindihan ninyo yung idea? So, paano ko gagawin ito?

**[1:28:06]** 3, 2, column operation, negative 4. I-delete ko yung 4 gamit yung pivot na 1. Excuse me. Yung nasa labas ay negative sign. Ako sinisulat ko negative 1 para yung negative sign lang kasi nadidelete siya eh. I mean... na ano siya, nasasama siya sa equal sign. So ako, I put negative 1 as a whole para hindi ko siya makakaligtaan or visible siya. Okay, so let's do the arithmetic. Yung first two column will not be changed at all. Diba? Ito na lang. So, mumultiply natin ng negative 4 ngayon ito. positive 4, bago mo i-add sa 5. So, magiging 9 po ito.

**[1:28:51]** Ito, of course, magiging 0, that was the intention. Negative 4 times 3, negative 12 plus 8, negative 4. And now, I am now free! to use a cofactor expansion once again along the second row. That's very bright. Diba? So, ang may iwanan, 1 times anong position ng 1, 2 plus 2, buburay mo yung second row, second column. We're now left with negative 4, 9, negative 3, negative 4. Are we good?

**[1:29:35]** Oo, 2 by 2 na lang. Imaginin nyo yung mga pinagdaanan nyo na maiiyak ka na lang, parang pakinamdam mo grumaduate ka, no? I mean... For example, sa exam, binigyan ko kayo ng 5x5, diba? Tapos na-reduce mo siya into 2x2. Naku! Masaya pa sa, kapag nagawa mo ng tama yan, masaya pa kesa yung graduate ka nung college. Sige, gawin natin to. Finally, the answer is negative 1, positive 1 to guys. So, magiging 16 minus negative 27. Oh, you see? The determinant is I don't know. Oh, takay lang yan talaga.

**[1:30:19]** Ano ba yung 16 plus 27? 3013. So, 43. Negative 43.

**[1:30:29]** Tama ba yun? Tama ba yung calculation ni sir?

**[1:30:36]** Well, let's try to verify our answer through calculators.

**[1:30:48]** I hope nakapag-download kayo ng kanya-kanya yung calculator ha. Kaya lang, unfortunately, yung mga standard na calculators... Sa classroom calculators, walang ganito eh. Yung mga dinadala nyo sa classroom, hindi yata ito available. Karaniwan mga apps sa cellphones. And, kahit na i-allow ko yung mag-calculator, hahanapin ko pa rin yung solutions ninyo sa pag-exam. gawin natin, negative 1, 3, 5, 2, 0, 1, 0, 6, 1, 3, 4, negative 7. Kinakabahan ako, baka mali na naman.

**[1:31:34]** Isang entry na lang, tama kaya? Yay! Ito sa answer, tama ba? Negative 43. So the determinant is really negative 43.

**[1:31:50]** Okay. Let's move on to the next one. And this is even nicer. Anong size na ito? 5x5. Ayan. 5 by 5. Sige, tingnan natin. Ay! By the way, guys, alam nyo ba yung another meaning ng negative 1 raised to i plus j? Alam nyo yung negative 1 raised to i plus j sa linear algebra, guys? Ano lang yan? Ang ibig sabihin lang neto, chessboard pattern. positive 1, negative 1, positive 1, negative 1, negative 1, positive 1, negative 1, positive 1, negative 1, positive 1. Nakuha nyo?

**[1:32:39]** Yun lang ang meaning ng negative 1 raised to i plus j. Kaya kapag halimbawa nasa 2-3 position ka, negative siya. positive yung nasa 1, 1 and then from there mag-e-emanate ka by alternately switching from 1, negative 1, 1, negative 1, 1, negative 1. Yun siya ha? For your information, kung let's say ayaw nyo nagkakalculate ng negative 1 raised to i plus j, gusto mong tignan lang from the matrix, halimbawa tignan nyo ito. nage-expand ka, for example, along this row, ayaw mong kumpitin to, pwedeng magsimula ka dito, positive, negative, positive, negative, so negative siya.

**[1:33:23]** Naintindihan ninyo, yung negative 1 raised to i plus j is just the checkerboard or the chessboard pattern. That's just another information, for your information only. Let's try the second one. Itong exciting kasi tingnan nyo, no? Medyo marami ang zero, so in fact, dito pa lang, kitang-kita na sa column 2, no? Kitang-kita nyo sa column 2, isa lang ang buhay dyan. So, maybe we can try a column expansion this time. Huh? So, if we expand along the second column, isa lang ang mabubuhay.

**[1:34:03]** 1 times negative 1 raised to 1 plus 2 kasi nasa 1, 2 position siya. Okay? Anong may iwanan? Buburahin mo yung 1, 2. 9, 9, 9, 2. 4, 0, 5, 0. 9, 3, 9, 0. 6, 0, 7, 0. But then again, You found that in the resulting determinant, meron na namang isang column na isa lang ang entry, no? Nice! Nice ba talaga?

**[1:34:47]** Diba? Akwa niya? So you can further expand along the fourth row. So, you know guys, yung nasa labas, negative 1 lang siya. So, 2 times negative 1 raised to, anong position niya? 1, 4. 1 plus 4. Kung gusto mo lang yung sign, plus minus plus minus yan. Okay? So, delete the first row and fourth row, you'll get 4, 0, 5, 9, 3, 9, 6, 0, 7. Nice! Kasi ito ay meron na namang column na isa lang ang entry.

**[1:35:31]** Diba? Nakita nyo how nice this determinant is? column 2. Ano ba yung nasa labas na? Negative times negative, so positive 2 na lang yung nasa labas. Isang entry nilang 3, tapos ang position niya ay 2 plus 2 this time, burahin mo ito, oh, 4, 5, 6, 7. There you have it. Naging 2 by 2 na lang siya. From 5 by 5, it now goes down to a 2 by 2 case. So, 6, yung nasa labas, tama ba si sir? Then this is 28 minus 30, is that correct?

**[1:36:21]** Tama ba? It is. negative 2 times 6, the determinant is negative 12. Okay? Nasundan nyo ba? Alam nyo sa exam guys, ang mga exam problem ni sir, hindi nyo pwedeng sabihin mahirap eh. Actually, I think yung nasa exam nyo, nagbigay ako ng 5x5. But you know, ang mga exam, ang exam natin ay mas leaning ako sa mga ganitong klaseng tanong. Nakita niya na minimal lang yung computation kasi I am more leaning into kung alam nyo ba yung mga properties. at alam nyo kung papaano sila gamitin to your advantage.

**[1:37:10]** Yun actually ang chinecheck ko. Kaya you may find na ano, 5x5 yung binigay ni sir but in reality hindi talaga yun mahirap. Akala nyo lang mahirap. Pag alam nyo gamitin yung mga QREMs and properties to your advantage. mataas ang score ninyo sa exam. Hindi ako nagbibigay talaga, yung mga ganito nga, for example, yung ganito kalala, medyo hindi ako masyadong nagbibigay ng mga ganyan ka random na items in the exam. I normally give more leaning to give problems like this. Naintindihan nyo ba yung ibig sabihin ko? Kasi, hindi, ang goal kasi nung exam, hindi naman tayo pagalingang mag-multiply, mag-add, kasi that is something that I cannot do as well, na?

**[1:37:59]** What I wanted to test is your ability to use the theorems and the concepts correctly. Na, yun yung aking gustong i-check kapag ako'y gumagawa ng problems in the exam. Alam nyo ba yung mga basics? Usually basics lang talaga. Mahilig din akong gumawa ng mga problems na mukhang mahirap pero pag... alam mo yung mga properties, hindi siya talaga mahirap. Kagaya neto, diba? Nakaka-intimidate yung 5x5. Pero tatandaan ninyo, lahat ng problems ko sa exam ay intentional. Ibig sabihin, hindi ko yan basta hinugot lang somewhere.

**[1:38:43]** Alam nyo ba yung mga ganita example? Ako nag-iisip lahat nyan. Iniisip ko lahat, while making the problems, iniisip ko, ano bang mga iisipin ng mga sudyante pag nakita nila to? I take that into consideration. You may think that, ah, kasi ang, yung ibang teacher, di ba, kukuha ng mga lumang libro, or maghahanap sa internet, ako no. I personally make may exam problems based on paano tumakbo yung lectures natin in everyday lectures. Ayoko kasing ano, minsan kasi kapag kumuha ka lang randomly in the internet or ano siya, magiging random din na I mean... yung baka hindi mo masukat yung gusto mong masukat in the exam.

**[1:39:36]** Ako kasi pag nagpapa-exam, gusto ko talagang makita kung how much have you learned, no? Natutuhan nyo ba yung gusto kong matutuhan nyo? Kaya nga nasabi ko, more than the computations part. mas gusto kong matutuhan ninyo yung mga principles, yung mga concepts, yung mga techniques instead of the manual computations. Okay, meron pa isang example. Ano yan? Given the matrix A, determine the values of the scalar lambda such that the matrix lambda identity minus A is singular. Oh my god! So ano bang itsura nung lambda ay minus A?

**[1:40:25]** Ano bang itsura nung lambda ay minus A? Compute natin. Lambda, yung identity guys ay ganito. minus A,

**[1:40:46]** okay? Pag minultiply mo yung lambda, mapupunta lang siya dito sa diagonal, di ba?

**[1:40:55]** Kama ba si sir? Did I do it correctly? O tas i-subtract, okay? Lambda minus 3, 0, negative 3. 0, lambda minus 3, 0, negative 3, 0, lambda minus 3.

**[1:41:23]** Is this correct?

**[1:41:27]** Amabang computation is our, sa lambda i minus a, okay? Alright. This is a square matrix. Anong alam natin sa, kailan daw ang tanong? Kailan daw ito singular? According to what we have learned that is going to be singular precisely when its determinant is zero. Diba kailangan ang determinant zero para singular? Okay, kumpitin natin yung determinant. We will make this, or we will equate this to zero, then we try to solve for all the possible lambdas.

**[1:42:11]** But you know guys, ayan na naman, no? May surprisingly may row na maganda. Kasi isa lang yung non-zero entry, is that correct?

**[1:42:26]** So that's lamb, redu, that's reducing to lambda, ay, yeah, lambda minus 3 times negative 1. The position is at 2, 2. Just delete those.

**[1:42:45]** Were you able to follow? It can delete me sir.

**[1:42:53]** Okay, nakasunod. Positive 1 lang naman to, so, lambda minus 3. Ito, mag-ano na lang si sir, yung 3's cross method, hindi ko napapasakitin yung ulo ko, no? So, it's basically lambda minus 3 squared minus 9.

**[1:43:17]** dahil tayong mag-solve ng equation, hindi ko i-multiply yan. And did you notice? Ito ay sum ng difference ng two squares. Did you see that? It's a difference of two squares. Anong naaalala natin? Buti nalang bright ka, no? Aha! Ito yung laman ng isipan mo, yan. Yan ang laman ng isipan mo, wala. Charat. Saan nga equal yung a squared minus b squared? Saan nga equal ito guys? Dapat maalala mo to. Ano to eh? Di ba?

**[1:44:01]** Hindi siya basta-basta, di ba? Tama ba yung memory ni sir? If my memory serves me right, it should be equal to that. Right? So if you think of this as a squared minus b squared, you can rewrite this as what? Lambda 3 minus 3. Diba? times lambda minus 3 plus 3 equals 0. And when you try to simplify, you get lambda minus 6 and here we get lambda equals 0. Now what's the theorem?

**[1:44:48]** over here. Pag ang product ay 0, ibig sabihin nun either of the factor is 0. So lambda is 0 or lambda is 3 or lambda is 6. So this is our answer. So there are three possible values of lambda. that makes the matrix lambda i minus a singular, okay? Alam nyo kung ano yung tatlong lambda na yan? Yung lambdas na yan, yung lambda equals 0, 3, 6 are called the eigenvalues of a. ganyan natin yung co-compute yun in the future. Oh my good lord.

**[1:45:38]** Nawala na naman yung aking screen, right? Is that correct? Tensya na kayo. So nagcrash na naman yung app sa aking ginagamit. I will have to use the native app of my computer. Kaya lang kasi pag native app, hindi ko nakikita kayo. So I have to open my other device para makita ko yung mga chat kung meron man.

**[1:46:10]** Can you now see my desktop? Yan.

**[1:46:19]** Alright. Ito na yung aking screen one more time. Ang tawag natin dito sa tatlong... constants na to, or scalars na yan, guys. We call them the eigenvalues of A. We will call them the eigenvalues later. It will be a topic in the future. Ano ba yung mga eigenvalues na yan? Ang mga tao, di ba? Lahat ng tao may kanya-kanya mga DNA sequence. Alam niyo yung mga DNA sequence? Kumbaga, yung DNA sequence will tell you your traits, saka program ka to evolve in a certain manner based on your DNA. Kung ang tao may mga DNA, ang mga matrices may mga eigenvalues.

**[1:47:04]** Kasi guys, alam nyo ba? Pag alam nyo yung tatlong eigenvalues na yan, these three eigenvalues will tell you all about the traits and characteristics of these matrices. Maraming tanong tungkol sa matrices tungkol sa isang matrix, ang masasagot mo, once na alam mo yung mga eigenvalues niya. Gaya nga nang sabi ko, parang ito yung DNA ng mga matrices. Kaya kapag ang mga matrices may similar na eigenvalues or pareho ng eigenvalues, most likely same sila ng characteristics. I will be more clear about this in the future. We will reserve that idea for a future lesson, okay?

**[1:47:49]** Inintroduce ko lang sa inyo that computing eigenvalues requires you to use determinants. Kaya hindi nyo lang dito sa lesson na ito huling makikita yung idea ng determinants. Okay guys? Naintindihan ba?

**[1:48:11]** Okay. Alam nyo ba may nagtanong sa akin, sa isang section yata, yung sa ibang section? Kasi dati, meron tayong method sa paghahanap ng inverse, diba? So let's say, nalaman ko ang determinant ng A ay hindi zero. So ang conclusion mo, aha, A is non-singular. But how do you find the inverse?

**[1:48:39]** Meron tayong method, ang sabi natin, maglagay ka ng identity sa kanan nya, i-RREF, dahil nga non-singular yan, yung portion na may A, magiging identity, tapos may lalabas dito na matrix, yun yung A inverse. Do you remember this concept? Ganyan yan talaga sa totoong buhay, no? May nagtanong sa akin sa chat, sa MS Teams. Natutuwa ko pag may mga nagchat-chat sa akin, especially tungkol sa subject matter. Sabi, Sir, meron ba tayong formula for A inverse?

**[1:49:20]** The question was, is there a formula for A inverse or an explicit formula. As in formula kung paano kukumputin yung A inverse. And you know what's the answer? Yes, there is. Na? May formula pala sa A inverse. Pero guys, itong formula na ipapakita ko sa inyo is just a formula. I'm not saying that it is easy to compute using the formula. At kung ako ang tatanongin ninyo, I will stick with this one. Kasi this one is quite organized. No?

**[1:50:00]** I mean, may formula tayo, yes, pero yung ipapakita ko sa inyong formula, hindi rin siya... friendly to use, in actual use. Do you get what I mean to say? Kung ako yung tatanungin ninyo, I will still stick with the old method or the Gauss-Jordan kasi ang maganda rin kasi nga, the idea is yung Gauss-Jordan gumagana siya sa kahit na anong problem sa linear algebra. So, yun na lang ang kailangan nyong alalahanin. Wala na kayong kailangang tandaan na iba. But if you are just curious kung meron bang formula for your inverse, yun yung susunod na ipapakita ko sa inyo. But before talking about the explicit formula itself, meron muna kayong kailangang matutuhan.

**[1:50:47]** Ano yung kailangan nyong matutuhan? Kailangan nyo munang matutuhan yung tinatawag na adjugate of a square matrix. Minsan tinatawag na adjoint, pero ako I don't like to call it the adjoint. I'd like to call it the adjugate of a square matrix A. Paano pa kinocompute yung adjugate of a square matrix A? Di ba marunong na kayo kumuha ng cofactor? Di ba? Capital A to ha. Di ba marunong na kayo kumuha ng cofactor? Yung cofactor na AIJ, ng AIJ ay ito.

**[1:51:26]** Yung MIJ yung matrix na maiiwanan pag binura mo yung row i at row j. Ang gagawin nyo, pukunin mo yung cofactors ng lahat ng entries, ia-arrange mo yung matrix, tapos itratranspose mo. Oh my good lord! Can you imagine? How many operations do you need to do para magawa ito? Dami, no? Tama? Halimbawa, magbigay tayo ng 3x3. 3x3 muna, para makita nilang kung gaano kahirap siyang ginagawa. Ito yung matrix ko.

**[1:52:18]** Paano kinocompute yung adjugate? Yung adge A, yung tinatawag, it's a very complicated matrix to compute. Kasi alam nyo guys, kukunin yung cofactor nung A11, kukunin yung cofactor nung A12 pero dito nyo ilalagay. Bakit nandun? Kasi tinatranspose natin. Nakuha nyo, so yung A13 cofactor nandito ngayon. Did you see that? Itong row na ito, naging column siya, cofactor. So kung ilang entries yan, ganun karaming cofactors ang kukunin mo, o diba?

**[1:53:00]** hindi siya, I mean, una sa lahat, hindi ito madaling computin. But we will do an example just for an illustration but in practice, nobody does this. Okay? So that's the adjugate of a matrix. And why do you think we would like to get the adjugate in the first place. Para saan ba itong adjugate na ito? Remember, pag tayo nagde-define sa linear algebra, most likely may reason behind this definition. So let me just put this computation over here and let me resize it para hindi masyadong malaki, eh. Let me just, at yung maganda sa online class, eh, no?

**[1:53:52]** Mahil po gawin sa [school], kasi electric pan nga, wala, eh.

**[1:54:00]** Yan. Kaya guys, alam nyo, ayoko rin, sa totoo lang, ayoko rin ng face-to-face, kasi, ah, yung lagkit ba? Classroom. Simula nang nauso yung online, ang hirap hirap bumalik sa face-to-face classes, lalo na sa subject na ito, I will have to bring a computer, I'll have to set up a projector, tapos napakainit sa classroom, yung computer mo nadudumihan. Yung mga ganun bagay, so... yun yung mga considerations. Kaya kapag linear algebra as much as possible during lectures, I'd like it to be online. Pero, I hope makapag, lalo na yung siguro yung mga lessons na hindi masyadong ma-computer, kapag face-to-face time matry natin.

**[1:54:46]** Okay, anong reason ba't natin kinocompute yung adjugate. Meron kasing magic yung adjugate, guys. Tingnan nyo. Subukan nyo i-multiply yung original matrix sa adjugate. Okay? Umultiply ko sila ha. Lalagay ko dito yung A11, A12, A13, at may liit yung boses. Sige. A32, A33, A11 cofactor, A12 cofactor, A13 cofactor, A21 cofactor, A22 cofactor, A23 cofactor, A31 cofactor, A32 cofactor, A33 cofactor.

**[1:55:36]** Okay. Pag minultiply mo sila, guys, tignan nyo lang ito, ito, ito, ito, ito, yung nandito muna, okay? Ano yung lalabas dyan? Malalabas dyan, guys, ay A11, A11 cofactor, A12, A12 cofactor, A13, A13 cofactor. Is it familiar? Does this look familiar?

**[1:56:12]** It is, kasi you know what this is? This is the cofactor expansion along the first row of A. So, basically, the sum is just the determinant of A. Kaya ang nandito, makikita nyo yung determinant ng A.

**[1:56:38]** Okay. Hindi ko kayo bubulahin, hindi ko na kayo bubulahin. Kapag second row, second column, ganon din yan. Ito naman ay cofactor expansion along the second row. Tapos, third row, third column, cofactor expansion along the third row, yan yung lalabas. E anong lalabas dun sa iba? Guys, halimbawa eto, pag first row, second column, A11, A21, cofactor, A12, A22 cofactor, plus A13, A23 cofactor. Ano kaya to? Saan kaya equal to?

**[1:57:26]** What do you think? What do you think? What do you think?

**[1:57:37]** Mahirap tong isipin. But let me tell you kung ano yan, ah, paano ba? Titigan nyo yung matrix na ito, titigan nyo yung matrix na M,

**[1:57:51]** okay? Okay, 1, 1, kukopihin ko lang si A, except, yung second row, gagawin kong identical sa first row,

**[1:58:18]** nakuha nyo. Of course, anong determinant ng M? Kapag may identical rows ka, determinant niyan 0, diba? Tama. But, guys, if you do a cofactor expansion along the second row in this case, if you do If you do, let's say, a cofactor expansion along the second row. So, ang lalabas, A11, cofactor, hindi ng A11, kundi nung position, nung entry na nari dito. Yung position kasi na ito ay A21, di ba?

**[1:58:59]** Nakuha nyo. yung cofactor nung position na yun, hindi nung entry na yun talaga. A12, A22, cofactor, A13, A23, cofactor, yun yung nasa taas. San equal yan? zero.

**[1:59:23]** Okay? Zero. And you know guys, if you do all of this, lahat ito magiging zero.

**[1:59:34]** So ano yung magandang balita? Ang magandang balita, kahit na, wait lang, wait lang, wait lang. Kahit na mahirap kalkulahin yung adjugate na yan, it is a nice matrix kasi guys, the real deal is, pag minultiply mo yung matrix sa kanyang adjugate, ang lalabas pala ay diagonal matrix na ang nasa diagonal entries ay yung determinant ng A. In short, yung determinant ng A minumultiply mo sa identity matrix.

**[2:00:19]** Take note nyo to.

**[2:00:25]** Naintindihan ninyo? Pag minultiply mo yung A tsaka yung adjugate nya, ang lalabas ay diagonal matrix na ang nasa diagonal entries are the determinant, ah, well, isa lang, yung determinant ng A. Can you see this? Yan yung lalabas na product. Okay? Naintindihan ninyo? how it extends naturally sa n by n na case, ganyan siya. Eh bakit ito mahalaga? Kasi sir, pag si A ay non-singular, syempre alam natin ang determinant ng A ay hindi 0. So pag hindi 0 yung determinant ng A, pwede kong i-multiply si A sa 1 over the determinant of A times the adjugate.

**[2:01:17]** And when I do this, the scalar will come out, ang umultiply si A tsaka si adj A. Saan na equal yung A times adj A? Nakasabi ko lang, it's determinant of A times the identity. Aha! Magka-cancel to. May iwanan identity. Kaya sa corollary, yung matrix na ito, kung ang product niya with A is the identity, it has to be the inverse of A.

**[2:02:01]** Nakuha niya? So, kung ang tanong ninyo, Sir, anong formula para sa inverse of A? Ito po yung formula sa inverse ng A. Ang tanong ko naman sa inyo, would you like to use this? Ikaw na lang. Kasi tignan ninyo, ano yung mga kailangan yung pagdaanan para lang makompute ninyo yung A inverse using this formula? Una, dapat alam mo yung determinant ng A. Pangalawa, dapat alam mo yung adjugate ni A. Paano ba kinakompute yung adjugate? Oh no! Kunin mo yung cofactors nung lahat ng entries, tapos itatranspose mo pa, lecheng yan. Nakuha nyo, hello?

**[2:02:47]** Pero alam nyo guys, madali ito kapag 2 by 2 lang. Meron tayong formula kapag 2 by 2. Kapag 2 by 2, madaling kunin yung inverse. ganito na, so let's say si A ay 2 by 2.

**[2:03:07]** Alright. Gusto natin non-singular si A, so ang determinant ng A dapat ay, ano dapat ito? Dapat ito ay hindi 0, okay? So kukuni natin yung adjugate ni A. So, paano natin kukunin yung adjugate ni A? Kukumpitin natin yung cofactor nung bawat entry. So, limbawa, anong cofactor nung A11? Ang formula po, negative 1 raised to 1 plus 1, buburahin mo yung 11, ang may iwanan na lang, A22.

**[2:03:48]** Nice na. Did you see it? Hello? Did you see it? Anong cofactor ngayon ng A12? Taping nga nyo ha, yung arrangement ko, first row, tinatayo ko na para naka-arrange na kagad sa adjugate, okay? A1, 2, negative 1 raised to 1 plus 2, burayin mo yung 1, 2, 1, 2, ang may iwanan, A2, 1. So insert ito yung negative A2, 1. Okay? Second row tayo. Anong cofactor ng A2, 1?

**[2:04:29]** negative 1 raised to 2 plus 1, 2, 1. Kung may iwanan na lang, A1, 2. So, negative lang ito ng A1, 2. And finally, ano? A2, 2 cofactor, negative 1 raised to 2 plus 2, 2, 2. Ang may iwanan ay A11, so positive 1 yan kaya A11. So therefore, ano yung edge A? Ito, a-arrange mo siya, A22 minus A21 minus A12, A11. So, therefore, ang inverse ng A kung 2 by 2 ay 1 over the determinant times

**[2:05:31]** this adjugate. Ito yung adjugate mo kapag 2 by 2.

**[2:05:39]** If you look at the formula carefully, so ito na yung 2 by 2. formula for the inverse. If you look at this carefully, hindi naman masyadong nalalayo yung inverse doon sa original kasi anang nangyari talaga dito guys? Look at the diagonal. The diagonals just switch, nagpalit lang ng positions yung diagonal, tapos yung other entries nag-negative lang. Nakuha nyo, yung sa anti-diagonal, yung sa other diagonal, magne-negative lang ang entries. And do not forget 1 over the determinant as an outside scalar factor. Example? Gusto nyo ng example? Halimbawa?

**[2:06:23]** Si A kunwari, 2x2 lang tayo kunwari. O, magbigay kayo ng paborito nyong number,

**[2:06:35]** ha? 6, 9, 6, 7, yan. Mga paborito natin yan, di ba? Yan. Parang yan yung matrix ninyo. Kunin nyo yung determinant. Ano yung determinant guys? So, determinant is 6 times 7 minus 6 times 9. So, this is 42 minus... Ano ba yung lecheng to? Help! Help! Help! Ano yung 6 times 9? Ano ba yun? 54 ba yun? Hello, 54. Yes. 42 minus 54. It's negative 12 ba to? Is it negative 12? Thank you. Okay.

**[2:07:18]** So therefore, A is non-singular since the determinant of A is negative 12 and it's not 0. Kung 2 by 2, hindi nyo na kailangan mag-RREF to get the inverse. Anong formula natin? 1 over that A times edge A,

**[2:07:44]** okay? 1 over that A, times edge A, so that's 1 over negative 12, times, parang kinuko yung edge pag 2 by 2. Anong turo ko sa inyo? Pag 2 by 2, just switch this to, mag-introduce ka ng negative sign doon sa dalawa. Did you get that? yun yung mnemonics, no? Pagpapalitin nyo yung main diagonal, tapos yung other diagonal, ininegative nyo lang. So magiging 7, 6, negative 9, negative 6. Isn't it nice?

**[2:08:25]** 9 over 12. Putang yun yun. Sabi, 9 over 12. 3 fourths. Init na ulo kasi eh, no? Hindi mo na kumputen. One half, ah, negative one half. Oh my good lord. Imaginin mo kung mag-a-RREF ka, tapos yan yung mga numbers na lalabas, di ba? Ayan. May advantage naman din yung formula na ito. Yung nga lang, guys, yung formula na ito, karaniwan ginagamit lang natin dito sa 2 by 2. Kasi alam nyo, pag 3 by 3 na yan, oh my good lord, kayo na lang, huwag nyo na ako isama. So halimbawa ito.

**[2:09:07]** show that A is non-singular, calculate the adjugate, and of course, the inverse. So, paano muna yung show that A is non-singular? Maybe you can use the determinant, anyway, you will use that in the inverse, okay? Sige, paano muna yung determinant ng A? Let's write the solution. Wala yata akong nakatype, wala nga akong nakatype na solution. Punyeta. Okay. Let's type in the solution. Lapit na tayo matapos guys. Tingnan nyo o, two slides away. Dismiss ko kayo na maaga today. Wee! Mahaba ito eh.

**[2:09:53]** Mahaba ito. Punin muna natin yung determinant ng A.

**[2:10:05]** O, pwede yung mag cofactor expansion right away but ako I will not. Ang gagawin ko, ang gagawin ni sir, gamit ito, I can eliminate that. Now, I can do E21, negative 1 but in columns.

**[2:10:28]** So, to be, parang insert sinosubtract, no? It means column 1 minus column 2 so 2 pa rin ito, 0, positive 2. Then the rest will not be affected. By doing so, I was able to reduce it into a single 2x2.

**[2:10:55]** Didelete ko siya.

**[2:11:00]** Is my computation correct? Let me just put it here para may space pa tayo dun sa educate. Is that correct? Is this correct? So, this is all in all, 6 minus negative 2. This is, what the fuck? 8 undeterminant. Tama ba?

**[2:11:27]** A is non-singular. Tama ba si sir that 8 is the determinant? Kaya non-singular talaga si A? Okay, sige. Sige, gawin natin.

**[2:11:45]** Alright. Ilagyan ko na linya para hindi tayo maguluhan. Ito na yung sinasabi ni sir, pag 3x3 na medyo hindi na makatarungan, hindi naman sa hindi makatarungan, manageable pa rin actually pag 3x3. hindi nga lang siyang ginagawa pag 4x4 na or 5x5. Kasi, tingnan niya ha, anong cofactor ng A11? When you look at A11, uburain mo ito, di ba? Negative 1 raised to 1 plus 1, 1, 0, negative 2, 3. ilan yung gagawin mong ganito? Syam. Syam yan, guys. Nakikita nyo yung ano, yung complication na sinasabi ko?

**[2:12:32]** Okay? Sige. Kambitin na natin. This is basically 3. Okay? A1, 2. Pag A1, 2 ito, buburahin mo ito.

**[2:12:49]** 1, 0, 0, 3. Buti na lang, madadali lang din tong mga matrix na ito, no? Ay! Sorry, 1 plus 2 to. Kita nyo na, nagkamali ako na isang number, no? So, negative to, negative 3.

**[2:13:05]** A1, 3, cofactor, eto yun. So, 1, 1, 0. 1, 1, 0, negative 2. So I guess this is negative and, ah positive and negative 2, negative 2. So kung mapapansin nyo, ina-arrange ko, ito yung row 1. Tinayo ko yung row 1 kasi remember may transpose. yung adjugate. Kaya, ina-arrange ko na siya para nasaset na kagad sa isip ko na transpose. Hindi ako malilito mamaya. Gets nyo? So, tingin tayo sa row 2.

**[2:13:47]** A21 cofactor. Ito naman yun.

**[2:14:01]** Nakita nyo kung gaano kahaba?

**[2:14:08]** Nakita nyo kung gaano kahaba ito? So negative of negative 2, positive 2, is that correct?

**[2:14:19]** It's lengthy, right? Do you agree with me? Nakikita nyo na yung sinasabi ni sir?

**[2:14:30]** Pero sa mga matsatsaga... Yan, okay yan. Okay na okay ito. Pero yung mga katulad ko, na walang katsaga-tsaga. My good lord. Paano to? 2, negative 1, 0, 3,

**[2:14:50]** 6. Buti na lang madali-dali yung matrix natin. 2,

**[2:14:59]** 0, 0, negative 2.

**[2:15:10]** negative of negative 4, positive 4 ba yun?

**[2:15:16]** Ama. Next, third row,

**[2:15:25]** negative 1 raised to 3 plus 1,

**[2:15:31]** 0, negative 1, 1, 0, oh my good lord,

**[2:15:41]** positive 1. Tagal-tagal mong in-overthink na to, sa positive one lang ang sagot. Okay! Malapit na matapos! Yehey! Yehey! 3-2.

**[2:16:02]** Pero negative to, so... Negative 2. Ay! Bobo! Hindi to! Teka lang! Teka lang po! positive 1, negative 1,

**[2:16:22]** okay. Finally, oh Lord, God bless everyone. Kaya nga sabi ko sa inyo, nire-recommend ko ba ito? Hindi po. Pag pinakuha ko kayo ng inverse ng 3x3, huwag nyong gagawin to, nakakamatay. parang pagtawid sa, ano, sa [a busy road]. Ah, my good lord, 3x3 last na, tinatamad pa. Tamad na tamad talaga si sir, pagpasensya nyo na kapag mga ganitong usapin. Ah, 2, 2, okay.

**[2:17:04]** ilang 2x2 yan, sham? Kasi may sham na entry ka. Imaginin mo kapag 3, 4x4 yung matrix, para makuha mo yung adjugate, 16 na 3x3. Gusto nyo yun? Ayaw nyo yun, di ba? Di ba? Nakuha nyo? So, ano yung adj?

**[2:17:27]** Ayan na, naka-arrange na, in-arrange ko na siya, para sa inyo. 2, 6, 4, 1, negative 1, puchang yan o, ayop, ayop ka, leche, yan yung adjugate. Paano nyo malalaman kung tama yung adjugate nyo? Sige, one last question. Paano nyo maalaman kung tama yung adjugate ninyo? You can multiply it with A. Sige gawin ka ha. Ano ba yung A? 2, 0, negative 1, 2, 0, negative 1, 1, 1, 0, 0, negative 2, 3.

**[2:18:15]** plus yung odds, dito nyo ilagay. 3, 2, 1,

**[2:18:23]** negative 3, 6, negative 1, at negative 2, 4, 2. Ano to? Product ng A at odds A. Tignan nyo.

**[2:18:38]** First row, first column, 6 plus 2, 8.

**[2:18:43]** That's 4 minus 4, 0.

**[2:18:49]** First row third column, 2, minus 2, 0. Okay, wala ng plastikan. Ang lalabas dyan ganito. Nakita nyo ba? Ano yung 8 na yun na nasa main diagonal? Ano yung 8 na yun? Yun yung determinant ng A na kinumpit nyo kanina.

**[2:19:11]** Did you see? That's how you know that your adjugate is correct. Pag nag-appear na ganyan yung product nyo with A, kung nilabas nyo yung determinant. Eh, may tanong dito, ano pa yung A inverse? Wala na, madali na to, no? ang a inverse is just 1 over 8 times yung matrix na ito. It's really just a multiple of the adjugate. Yung multiple, reciprocal nung determinant. Okay, nasa sa inyo na Kung gusto nyong ipasok yung 1 over 8 sa loob, or manatili na lang sya sa labas, manahimik ka na dyan sa labas, parang awa mo na.

**[2:19:56]** Diba? Pwede na yan. Yan yung A inverse. Okay? Did you understand yung complication na tinutukoy ko that Although, there is an explicit formula for the inverse, this is quite impractical, especially when the matrix is large. Gauss-Jordan pa rin for the win. Do you agree with me? It's still the Gauss-Jordan algorithm. ang ating gold standard sa pagkukompute ng inverse. Simply because, ang laki ng chances na magkamali kayo dito sa iisang number.

**[2:20:39]** At saka paano kapag 4x4, 16 na 3x3 ang determinants na kukumpitin mo? Maawa ka sa sarili mo, no? ang una kasing ginagawa dapat talaga is to love yourself. Maawa kayo sa sarili nyo, huwag nyong pahirapan. I just showed you this to let you know that there exists such a formula. If you were just interested meron bang formula? Meron po. Pero it's really an impractical thing. hindi naman lahat ng formula sa MATH ay ano eh, ang tag nun maganda o ano. Huwag kayong maniwala sa nagsasabi na MATH is fun, MATH is easy. Hindi totoo yun. MATH is very dark.

**[2:21:23]** It's a very dark subject. Diba kapag mga bata kayo, kinakantahan pa kayo ng mga teacher nyo, math is fun, ganang-ganang. Hindi totoo yun. Ako as a math major will tell you that math is a very dark subject. Lalo na pag ikaw ay mathematician, you seem to feel like You are in a very dark room. Hindi mo alam kung saan ka papunta. Okay? Last but not the least, okay? Last application. Alam nyo ba kung may explicit formula para sa inverse? So, kung di ba naalala ninyo? meron akong linear system na ax is equal to b, meron tayong formula, kung si a ay non-singular, meron tayong formula para sa solution na x, ang formula ay a inverse times b.

**[2:22:22]** Is that correct? So anong ayun mangyayari kapag may formula ka sa A inverse, pwede mong palitan ito ng 1 over that A times what? Adds A times B. Tama ba guys? Diba?

**[2:22:47]** Ang tanong, saan equal yung numerator na ito, no? I mean, itong vector na ito.

**[2:22:57]** Let me show you kung paano yan magre-reduce. So, kung meron ka ngayon linear system na ax equals b, tapos yan ay yung coefficient matrix ay non-singular, meron na rin kayong explicit formula para dun sa unknown na x sub j, for j equals 1 to n. Ano daw? The formula reads as follows. Yung pang j na unknown, makakalculate nyo by what? dividing the determinant of AJ by the determinant of A, where, ano yung AJ?

**[2:23:42]** Si AJ, sya lang yung matrix A, i-replace mo yung column J by the vector B. What the fuck? Anong ibig sabihin nun? Anong ibig sabihin nun guys? Ganito, let me share, let me show you. Halimbawa, interesado ka sa X sub 1. X sub 1 na lang. Interesado tayo kunwari sa value ng X sub 1. Kasi yun yung sinasolve natin. Kailangan mong malaman yung matrix na A sub 1. Paano yung matrix na A sub 1? Di ba yung A? Ito yung first column. Okay? Ito yung second column nya.

**[2:24:30]** Okay? At ito yung last column nya. Ang last column nya ay AN1, AN2, ANN. There you go. To get the matrix A sub 1, yung first column na pula, buburahin nyo, ipapalit nyo yung B1, B2, Bn. Ano yung mga B na yan? Yan yung nasa right-hand side. Nakuha niya, kukumpitin nyo yung determinant ngayon yung A1. Now look at this. Pag kinumpit nyo yung determinant ng A1 guys, and you apply cofactor expansion along the first column, ito yung lalabas, B1, A11 cofactor, kasi A11 yung narin dito, diba?

**[2:25:26]** B2, A21, cofactor. Tama!

**[2:25:37]** BN, AN1, cofactor. But you know what this is guys? Ha? Alam nyo kung ano to? Tingnan nyo yung edge A. Ang edge A, ganito siya.

**[2:26:05]** Tensya na kayo, hindi ko kasi na i-type yung mga matrices na ito.

**[2:26:21]** Okay, pag minultiply ko siya sa B guys, pag minultiply ko ito sa B, pag minultiply ko edge A times B,

**[2:26:34]** ay makikita kayo dito eh.

**[2:26:39]** Anong makikita ninyo?

**[2:26:46]** Ito yun o,

**[2:26:53]** nakuha nyo.

**[2:26:57]** Itong unang, unang ano, yung unang, yung unang product na ito, yung unang dot product na ito, siya yung determinant ng A1. Nakuha? So, yung edge A times the vector B ang unang-unang entry nandito, ito yung determinant nung A2.

**[2:27:23]** Okay? Hello?

**[2:27:31]** Mahirap ba siya makita? Ay, ay, ay, ba't A2? Sorry, A1. Yung pangalawa naman, ito naman yung determinant nung A2. Ano naman yung A2? Yung A2, instead na yung column 1 ang papalitan mo ng B, papalitan mo naman yung column 2.

**[2:27:53]** Kasi ito AN,

**[2:27:57]** okay? Kaya kung ang idea is that yung X ay 1 over that A times edge A times B

**[2:28:13]** yung vector x ninyo will be 1 over that a times that a1, that a2, that an. Kung equal ito sa x sub 1, x sub 2, x sub n, so yung x sub 1 ninyo anong formula? yung determinant ng A1, di-divide nyo sa determinant ng A. Yung X sub 2 ninyo, pukunin nyo yung determinant na A2, di-divide nyo sa determinant ng A. And this is what we call as the Tim Cramer's rule. Charot! Hindi ito Tim Cramer, letter K yata sila, no? Ito ay letter C.

**[2:28:54]** Kramer, hindi ko alam yung first name ni Kramer, huwag nyo nang pansinin. So to further solidify your understanding of the Kramer's rule, meron ako maliit na example lang dito. Guys, maliit lang ito, para lang just to illustrate. Let's say, meron kang linear system na nakikita nyo na sumusunod, no? When you try to write it in the matrix form, sorry, yung coefficient matrix natin guys ay 2, 3, 1, 2. Yung unknown vector ay x sub 1, x sub 2.

**[2:29:33]** while yung column vector sa kanan, yung right hand side natin ay 2, 0. So that ang AX ay equal sa B. Now nakita mo just because you were curious nung kinumpit mo yung determinant ng A. ang lumabas ay, ano pong lumabas? Ang lumabas ay 4 minus 3 or 1. Is that correct? And because that 1 is not 0, you were able to conclude that A is non-singular. So according to the theorem, Tim Cramer's rule applies. Nag-a-apply kasi ang Cramer's rule only when that A is non-singular.

**[2:30:21]** Okay? Non-singular naman sa isang nag-a-apply ang Tim Cramer's rule. Paano kukumpitin, for example, si X sub 1? So x sub 1, mako-compute nyo by calculating the determinant of A1 divided by the determinant of A. Alam na natin yung determinant ng A that's 1. Yung determinant nung A1, kukunin mo si A, anong turo ko sa inyo? Kukunin mo si A, Papalitan mo yung first column ng B. Yung B, ipapasok mo dun sa first column, so magiging 2, 0, 3, 2, divided by 1, kasi 1 na yung determinant natin.

**[2:31:05]** So when you evaluate the determinant, this is 4. And x sub 2, Now, the determinant of A2 divided by the determinant of A. Paano naman yung A2? Coming from A, ire-replace mo yung second row naman by B. So, 2, 1, 2, 0.

**[2:31:31]** Did you understand? the Cramer's rule. So ito naman ay negative 2 po. Can you check kung talagang solution nga ba ito? Kung 4 at negative 2 to, gagana ba? Check nga natin. 8 minus 6, 2 nga. 4 minus 4, 0. Yay! Tama, na? So, they are really the unique solution. So, not only that, you know, you have a unique solution, the truth is, you now have a formula for the values of the unknowns, no?

**[2:32:10]** But again, gaya na sabi ko, We get to have a formula, but in reality nobody use this. Kasi when the matrix is large, this determinants can be cumbersome to execute, no? Hindi yan madali. Nagkataon na nagmukhang madali kasi nga yung example ko po dito ay two by two lamang. At syempre, may mga kapalit, no? May mga kapalit yung mga conveniences na ito. It is convenient because there is a formula But nevertheless, when you look at the formula, it involves taking determinants.

**[2:32:51]** And determinants of large matrices can be very hard to execute correctly. Especially when you have the pressure of the time, kapag nage-exam kayo, for example. Naintindihan ninyo? Hindi, hindi siya madali ring gamitin kagaya ng formula for the inverse. It is just good to know that there is a direct formula. Naintindihan nyo? Pero, um, hindi ibig sabihin nun na yan yung gagamitin mo in practice. Anong gagamitin natin? It's still Ghost Jordan.

**[2:33:30]** Gagawin mo pa rin yung augmented matrix na ito, TR or EF mo. Kasi ito isang step lang, isang mahabang step lang, but sure ball. Did you understand? If you just do it correctly, nandyan yung gusto mong sagot. malalaman mo pa, hindi mo na kailangan i-check kung non-singular o hindi, kasi ito'y gumagana ke non-singular or hindi si A. Ke square or hindi si A, itong RREF method ay gumagana. Nainundin niya niya yung aking point? No? Nainundin niya niya aking point? It is just fancy sa pakiramdam na meron kayong formula and all, but you know, alam nyo, napakalimited din naman ng application ng formula na ito eh kasi una dapat square and non-singular yung A. Kapag hindi na square yung A, hindi na to applicable.

**[2:34:25]** kasi wala ng determinant pag ganoon. Ang determinant, remember, square lang. Kumbaga, the idea is it is just good to know na merong formula but in reality, I will not use it. Maybe for a 2x2 linear system, I will use it but for the general case, I still will not use the Cramer's rule. Diba? Ayan, nakalagay good luck on long exam number one kasi ito ay tawag na ito. Tapos na. I mean, yung coverage ng long exam number one ay na-cover na natin. Kaya i-dismiss ko kayo na maaga. Tama ba ako?

**[2:35:10]** Maaga ba? Oo, no? Babawi tayo ngayon kasi for the last few weeks lagi tayong overtime. And for today, I think I'll have to dismiss you early. Next week, sasabihin ko yung mga guidelines. Ano yung mga dadalhin nyo sa exam? Kailan yung exam? Saan gaganapin yung exam? Ano yung mga gagamitin yung panulat or papel? So, sasabihin ko yan lahat next week, kaya huwag kang absent. At the same time, I will have to introduce the next lesson. Hindi na yun kasama sa long exam number one, but we are not wasting time. Okay?

**[2:35:52]** Ay, may Korean phrase dyan. [Redacted: personal aside about the professor.] Anggalin ko lang yung recording, ha?

