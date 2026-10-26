# MATH 018 Online Class: Gaussian Elimination, REF & RREF, Gauss-Jordan Method & Polynomial Interpolation (Transcript)
Instructor: professor. Recording is about 3 hr 0 min long. The transcript is in Taglish, as spoken (auto-transcribed with Whisper large-v3-turbo; expect occasional mishearings).

## Topics covered
- Recap: an m × n linear system is a conjunction of m linear equations in n unknowns (coefficients aᵢⱼ; the right-hand sides bᵢ are not counted in n). Values that satisfy all equations at once are solutions: consistent if one exists, inconsistent if none. He is hoarse, so he speaks softly all session
- 2 × 2 geometry: each equation is a line, and there are 3 cases: a unique intersection point, parallel lines (no solution), or coincident lines (infinitely many), e.g. x − y = 3 and −2x + 2y = −6 (−2 × the first). In general it is m hyperplanes intersecting in ℝⁿ (planes when n = 3)
- Equivalent linear systems have the same solution set. Two systems both solved by (1, 2): which is easier? Student said they are the same; student and student said #2, because 7y = 14 gives y = 2 at once, then x = 1. Goal: turn any system into an equivalent "nice" (upper-triangular) one with an algorithm a computer can run
- Gauss's 3 operations that keep the solution set: swap two equations (p ∧ q ≡ q ∧ p), multiply an equation by a NON-zero scalar (× 0 makes it degenerate, like silencing a friend's condition), and replace an equation by its sum with a scalar multiple of another (elimination)
- Worked example: 2x + 5y − 9z = −10, x + 2y − 4z = −4, 3x − 2y + 3z = 11. Swap eq. 1 and 2, eliminate x, then −8y, get 7z = 7, and back substitution gives the unique solution (x, y, z) = (2, −1, 1) (one vector, not three solutions). GeoGebra 3D: the three planes meet at that point
- Augmented matrix [A | b]: the computer does not understand x, y, z, only positions, so drop the unknowns (a missing variable has coefficient 0); the bar only separates the right-hand side
- REF ("echelon" = ladder of ranks; student: "levels"; military, faculty and corporate ranks): (1) zero rows at the bottom, (2) the first non-zero entry of each non-zero row is 1 (the pivot), (3) each pivot is to the right of the pivot in the row above ("falling ladder"). RREF adds: each pivot is the only non-zero entry in its column, so no back substitution is needed
- Classifying 5 matrices: A is RREF. B is REF but not RREF because of a −2 above a pivot (student said yes; student and student said no). C has a zero row in the middle and D has a leading −1, so neither is REF; the last matrix's pivots are not a falling ladder (a "shoe-rack" staircase). Not REF means automatically not RREF, even if pivots stand alone. His iPad and connection dropped briefly around 50:49–52:00 and 58:03–58:37
- Elementary row operations (class-only notation): Type 1 Eᵢⱼ swaps rows i and j; Type 2 Eᵢ(α), α ≠ 0, multiplies row i by α; Type 3 Eᵢⱼ(α) replaces row i by row i + α·(row j). A ~ B (row equivalent) if B comes from A by finitely many row operations, written with the operation above the arrow. Learn it by hand; use Gemini/ChatGPT to check your work, not just to comply
- On [1 2 −1; 3 4 0]: E₁₂ swaps the rows, E₂(−3) makes row 2 [−9 −12 0], and E₂₁(−3) makes row 2 [0 −2 3], i.e. x + 2y = −1, −2y = 3. "Walang problem sa linear algebra ang hindi masusolusyonan ng RREF": he calls this the most important lesson. No "elimination by erasure"
- Challenge: the RREF of [0 1 1 1; 2 2 0 6; 1 1 1 0; 3 3 1 6] via E₁₃, E₂₁(−2), E₄₁(−3), scaling by −1/2, E₂₃, E₁₂(−1), then E₂₃(−1), E₄₃(−1) (the class typed these in chat, all correct) gives [1 0 0 −1; 0 1 0 4; 0 0 1 −3; 0 0 0 0], so x = −1, y = 4, z = −3. A student caught his slip in the bottom row (its last entry should stay 6, not become 3)
- Exam tips: one wrong number ruins the rest; if numbers blow up you probably made an error, since his long-exam problems are designed to avoid big numbers and fractions (and he avoids special exams). The algorithm will later be a programming exercise. Facebook "apple + orange" puzzles are just linear systems
- Every matrix reduces to an RREF, and it is unique ("the RREF"; many REFs are possible). Row-equivalent augmented matrices mean equivalent systems. Gauss-Jordan method: augmented matrix → RREF → read off the solution (back-substitute only if needed). Ex. 1: x + 2y = −1, 4x − y = 5 with E₂₁(−4), E₂(−1/9), E₁₂(−2) gives the unique solution (1, −1)
- Ex. 2: x + 2y − z = 3, x + 3y + z = 5, 3x + 8y + 4z = 17 needs fractions: unique solution (x, y, z) = (17/3, −2/3, 4/3); check by substituting (left to the class). Screen dropped about 1:51:15–1:51:53. Around 1:53:45 he says it is already 12:30, so eat if hungry
- Ex. 3: x − 2y + 4z = 2, 2x − 3y + 5z = 3, 3x − 4y + 6z = 7 reduces to the row [0 0 0 | 3], i.e. 0x + 0y + 0z = 3 (degenerate, always false). Student: "0 is not 3", so it is inconsistent; student: the solution set is the empty (null) set ∅
- Ex. 4 (3 × 5): x₁ + 2x₂ − 3x₃ − 2x₄ + 4x₅ = 1, 2x₁ + 5x₂ − 8x₃ − x₄ + 6x₅ = 4, x₁ + 4x₂ − 7x₃ + 5x₄ + 2x₅ = 8 gives RREF [1 0 1 0 24 | 21; 0 1 −2 0 −8 | −7; 0 0 0 1 2 | 3]. Pivot columns give the leading variables x₁, x₂, x₄; x₃, x₅ are free, so there are infinitely many solutions
- Solution set of Ex. 4: x = (21, −7, 0, 3, 0) + x₃(−1, 2, 1, 0, 0) + x₅(−24, 8, 0, −2, 1), x₃, x₅ ∈ ℝ. Student caught that x₄ = 3 − 2x₅ (he had written 3 − 2x₄). Sample solutions: (21, −7, 0, 3, 0) and (20, −5, 1, 3, 0)
- Technology: NumPy has no built-in RREF, so use SymPy (`pip install sympy`, `from sympy import *`); `Matrix(...).rref()` returns the RREF plus the pivot-column indices, here (0, 1, 3), and `.rref()[0]` gives just the matrix. Calculator app: SHIFT 4 → row reduce (up to 7 × 7). Software uses a modified Gauss-Jordan (LU decomposition) to avoid division by zero
- Assignment: Example 5 (4 equations, 3 unknowns), by hand and with software, to be checked next week. Terms: m = n square, m < n underdetermined, m > n overdetermined. Polynomial interpolation: n points with distinct xᵢ give a degree n − 1 polynomial, found from the system with rows [1 xᵢ xᵢ² … xᵢⁿ⁻¹ | yᵢ] ("machine learning is just a math problem"). Example: (−1, −2), (0, 0), (1, 0), (2, 4) give p(x) = x³ − x²
- Tree height → weight: (1.5 m, 35 kg), (3 m, 45 kg), (3.8 m, 50 kg) give p(x) ≈ 24.2 + 7.5x − 0.2x² (by calculator), so p(2) ≈ 38.4 kg. Bring a scientific calculator to exams. 4.2 m is outside [1.5, 3.8], so interpolation cannot be used (extrapolation models are needed). Out of time at 1:30 with 3 slides left (when a system has a unique / no / infinitely many solutions), to finish next meeting

## Transcript
**[00:00]** record pala natin yung session.

**[00:16]** Okay, the session is now recorded, being recorded guys. Alright, so, bago tayong magsimula, irareview natin saan tayo na putol. So, basically, last meeting, we ended up here, no? Ano ba ito? Dito, dinidefine kung anong ibig sabihin ng isang m by n na linear system. Pag sinabing m by n, yung linear system, yung m dito, stands for the number of equations in the system. In fact, the number of linear equations.

**[01:00]** Lahat ito ay linear equations as you can tell. Yung N dito represents the number of unknowns ng bawat equation. Okay? Take note yung right-hand side na B ay hindi counted doon sa N, na hindi siya counted, kumbaga it's an additional set of scalars. Ngayon, itong mga numbers na to or mga scalars na to, they are called the coefficients of the linear system, yung mga A, I, J na yan. Tapos yung mga B na ito, yung mga right-hand side. As defined, ang isang linear system ay conjunction.

**[01:45]** Conjunction of M linear equations each in N unknowns meaning to say As propositions or as statements, these statements are by default connected by an end connector. Ginagamit natin yung end. Ngayon, because we are using the logical connector end meaning to say a conjunction is true only when each of the component statements is true. Correct? Kailangan lahat ng mga statement na components ng conjunction, dapat sila'y sabay-sabay na true. Kaya nga nang sabi ko sa inyo last time, imagine ninyo parang These are set of conditions that we need to satisfy. Parang may condition ako, may condition siya, condition niya, okay?

**[02:41]** So parang we have to settle on an agreement, no? Kailangan lahat tayo ay nag-a-agree. para masabi natin na satisfy yung linear system. At yung mga values ng unknowns that can satisfy the system are called the solutions to the linear system. Kapag may solution, sinatawag natin na consistent yung linear system at kapag walang solution. Makikita nyo, there is a possibility na walang solution later. Yun yung tinatawag natin yung inconsistent na case. Kabalik ka rin na consistent. So far, is the definition clear?

**[03:25]** Ganun ba kayong tanong sa definition? Before I proceed with the next few slides, I think familiar naman kayo, no? I mean, nakakita na kayo neto noon, yun nga lang, sa algebra pang bata, pasan siya naka, medyo malat ako, ha? Medyo hihinaan kayong boses ko, so I can continue talking for the rest of 3 hours. Ayan. Pero, at this level, can you still hear me clearly? Okay lang ba yung audio? Kung hihinaan ko ng konti kasi parang hindi tatagal yung boses ko pag nilakasan ko. Okay? Pasensya na kayo.

**[04:08]** nakita nyo na ito dati, except nung maliliit kayo, yung linear systems na ito ay maliliit din. For example, 2 by 2, when you say 2 by 2, meron kang dalawang equations, tapos dalawang unknowns, no? Maximum na yata yung tatlong equations with 3 unknowns, no? In linear algebra, we will be dealing with the general problem. When you say general problem, you have an arbitrary number of equations with an arbitrary number of unknowns. May 2100 equations yan, tapos lahat may 40 unknowns. Paano naman ito mag-appear in linear algebra? Makikita ninyo in the next few lessons why studying linear systems is important.

**[04:55]** Gaya nga nang sabi ko, you have already seen this in an earlier course in algebra. For example, if M and N reduce to the value of 2, and the field of scalars is set to R. The linear system in the previous slide reduces to this system. Can you see it, no? Kita nyo yun yung 2 by 2 kasi meron kang two equations. Bawat isa ay may dalawang unknowns. So, sa algebra pang bata, pinag-aralan ninyo yung different methods to solve for such a system, no? Do you recall that each of these linear equations represent a line in the Cartesian plane? Pinaplot nyo yung mga graphs na ito as straight lines, correct? Do you recall that?

**[05:46]** Nare-recall nyo ba na pair of straight lines ito? And the way we wanted to interpret the solution is paano nag-i-intersect ang dalawang or ang isang pair of straight lines in the plane. Well, we found out in earlier course there are three different ways a pair of lines can intersect. Let me show you. So the first scenario is when this pair of straight lines intersect at a unique point. And this unique point, ito, ito, tulayan ko ng ibang color, is the unique solution to the linear system. And you know, may pwede rin namang yung dalawang lines ay maging parallel.

**[06:37]** And in that case, hindi sila nag-intersect. So ito yung consistent unique solution, no?

**[06:46]** Okay? Ito namang pangalawa, dahil yung mga lines mo hindi nag-intersect, they say that there is no solution. So ito yung inconsistent na case. And then the third case, ito hindi ko lang ipakita sa inyo pero nakikita nyo medyo binold ko yung line. Kasi I wanted to show you that hindi lang isang line yan, actually yung dalawang pair of lines mo ay nag-coinside. Do you understand? Example, didi ako yung example, no? Halimbawa, yung equation 1 ko kunwari, x minus y equals 3. Tapos yung second equation ko ay negative 2x plus 2y equals negative 6. Sa simula, mukhang magkaiba yung dalawang linear equations na yan, right? But as you can see, yung second equation kasi it's just a redundancy of the first equation. Do you see that?

**[07:50]** You can actually obtain the second equation by multiplying the first equation by negative 2. Do you agree? Can you see that? And because of that, these equations are just equivalent, kaya kapag ipaplot mo sila, hindi totoong may dalawang magkaibang lines. Sa case na ito, yung dalawang lines mo ay magkapatong. Or they are really the same line. So when you consider the intersection, the intersection is, well, marami, yung buong line na yan. Kaya yung pangatlong case na to, at yung case where you get infinitely many, solutions. Kasi bawat point dyan sa line na yan, solutions.

**[08:40]** Did you understand? Hindi pa tayo nagsosolve, guys ha? Inaaral pa lang natin ang mga linear system qualitatively. Hindi pa tayo nagsosolve, okay? So, focus muna kayo dun sa concept. Itong first case, tsaka yung last case, ito yung consistent na case, diba? At itong second, ito yung inconsistent.

**[09:05]** Did you understand the two by two case? Hmm? In general, etong M by N linear system ninyo, you can think about this as parang meron kang M na hyperplanes na nasa loob ng Rn kasi yung mga unknowns natin ay may N components. meaning to say, yung intersection ng mga hyperplanes na ito ay nasa Rn. Para kang merong mga hyperplanes in Rn that get to intersect to one another. Kung ang n natin ay 3 guys, mga planes lang talaga ito na flat na nag-i-intersect sa space. Maybe we can show through GeoGebra later, through this simulation software later, kung anong itsura niyan kapag sa case when n is equal to 3.

**[10:02]** You understand? But of course, when n is greater than 3, wala tayong ano, wala tayong picture. for it, but nevertheless, you just think about it as a set of hyperplanes intersecting in an n-dimensional space. Did you understand? Okay, so let me now move on to this next definition. Here I am defining what it meant to say Kapag sinasabi natin, ang dalawang linear systems ay equivalent. So, pag sinabi natin, ang dalawang linear systems ay equivalent, ibig sabihin lang nun, when you collect all the solution vectors, they are literally the same set, okay? parehas lang na set of vectors yung nakakapag-solve sa kanila.

**[10:53]** So, for example, let's consider these two linear systems. Each of these are in two unknowns. Kahit yung pangalawa, mukha lang one unknown yung pangalawang equation but in reality meron kasi ditong 0x na hindi na natin sinusulat. Okay, guys? Naulawaan ba yun? Sa umpisa, when you look at them, well, your first equations are exactly the same. Itong dalawang, exactly the same. Nagkatalo sila dito sa pangalawang. equations. If you try, if you attempt to solve this using your elementary methods in elementary algebra, well, you will find out na may parehong solutions ito.

**[11:37]** In fact, I will show you the solution graphically. So, if you graph the first pair of lines, makikita nyo they both will intersect at the point 1, 2. Is my picture clear? Nakita nyo ba na sila'y nag-i-intersect sa 1, 2. Whereas, if I try to drop the second pair, magkaibang pair of lines but never the same, they also get to intersect. At the same point, 1, comma, 2. Kaya nga, in both of these linear systems, although they are different, yung solution set natin is the vector 1, 2. There is a unique solution for this case.

**[12:23]** Ang tindihan ninyo? yun ang ibig sabihin natin when two linear systems are equivalent, pareho sila ng solution set kahit na magkaiba yung mga equations. Pero ang tanong ko dito, sino dito sa dalawa? Which do you think of these two is easier to solve? based on your experience in algebra, which one is easier to solve? Is it linear system number 1 or linear system number 2? What do you think? And can you tell me the idea behind your answer, please? Sino sa dalawa, which do you think is easier to linear system number one, or linear system number two.

**[13:12]** You can answer by typing in the chat box, or if somebody has a microphone, maybe that's a better option. So yun nga, anyone? I would like to answer sino ang mas madaling i-solve yung number one or yung number two based on your experience and an idea why do you think it is your answer? Well, sabi ni student, same lang po sila in my opinion. Okay? Sabi ni student, number two. Okay. Sabi ni student ay number two. Sige nga, dun sa mga sumagot ang number two, would you like to tell me more? I mean, why do you think two is a bit easier to solve?

**[14:07]** Kasi alam niyo, yung susunod na portion ng discussion natin ay... patungo dito sa idea. Okay, student. Sabi ni student, obvious po yung value ng y. I think what he meant was that if you look at the second equation, 7y equals 14, the value of y is actually readily available. You just divide both sides by 7, you get y equals 2. And when you get the value of y equals 2, just substitute it to the first equation, you will be able to get the value of x which is 1. Naintindihani niyo? Unlike, when you look at the first equation, you will You know, alam nyo yung mga standard na ginawanag sa algebra.

**[14:48]** Gagawa ka ng mga algebraic calisthenics to be able to get a value of x or a value of y by, excuse me, by elimination. Ang tawag nyo doon, nag-eliminate kayo, right? Naalala niyo yung terminology? Huwag kayong mag-alala kasi later on we will have our own method to solve for linear system which is using Python. Charot. Hindi, meron tayong algorithm na i-develop. where the Python code is based on, yung algorithm ay ituturong sa inyo.

**[15:27]** Kasi alam ninyo, yung method na tinuro sa inyo ng pangbata, yung marami kayong tawag, may substitution, may elimination. Lahat yung mga method na yun kasi guys ay dependent siya doon sa maliit na size. Nagkataon lang na maliit kasi yung size ng linear systems ninyo nung maliliit kayo, kaya efficient yung mga yun. Pero pag kasi yung mga linear systems natin ay malalaki, we must have An efficient algorithm that will handle the computation. Syempre, sa totoong buhay, hindi naman talaga yan ginagawa by hand, gaya ng sabi ko, no? We will have to put it in the computer, but we have to understand how the computer will do it, no? Kasi, kayo yung magpa-program, di ba?

**[16:16]** For example, hindi ko na muna ipapakita but these two linear systems are actually equivalent. One is nicer, kagaya ng previous example ko, no? The second one is nicer. Why? Why do we think the second one is nicer? Because the second one is actually readily solvable, right? If you look at it, alam na natin yung value ng z. And then from that, you can use the second equation, substitute that value of z, you can get y. Now that you know y and z, you can substitute both of them to the first equation to be able to get x.

**[17:01]** Did you understand the idea? Ang maganda dito, so these two are equivalent, right? Ang maganda dito, dahil sila'y equivalent, pag sinuald ko ito, It is like solving the original linear system. So, the question now remains is how do I turn a regular linear system like this, so this is a very generic looking linear system to an equivalent linear system that has this yung tinatawag natin nice na form. So, paano natin yan ito turn into an equivalent nicer form?

**[17:45]** Do you get the idea of the lesson for today? yun yung ating trabaho dito. Kapag meron kang generic na linear system na rectangular na ganyan, how do we turn it into something like this? If you try to look at this in the point of view of a matrix para itong upper triangular na, right? Can we do that? Sabi ni Gauss, yes. Kasi, according to Gauss, there are three different ways, there are three different operations that you can do on a linear system without changing the solution set, without affecting the solution set.

**[18:26]** You can do any of these three. without really modifying the solution set. So in other words, nag-pro-produce ka lang ng equivalent na linear system. Ano yung tatlong operations na yun? Number one, you can swap two equations in the linear system and the meaning does not change. Why is that true? Kasi diba sa logic, Sa logic, ang PNQ kasi, equivalent lang naman siya sa QNP. Kumbaga, in a conjunction, yung order ng mga statements is immaterial, diba? Kung true yun true, kung false ay false, no? Regardless kung guguluhin mo yung arrangement ng mga statements.

**[19:08]** Do you agree with me? Therefore, if you have a linear system and you swap any two equations, does that change the logic of the statement? The conjunction? Not really. Okay? Number two, you can multiply both sides of an equation by a non-zero. scalar. Ah, well, this is algebraically true kasi kapag meron kang dalawang bagay na equal, let's say x is equal to y and you multiply sum a basta as long as it's not zero These two statements are equivalent.

**[19:48]** Equal pa rin yan. At dahil nga ang a ay hindi zero, maibabalik mo siyang pa ganon kasi you can divide both sides by a. Maiko-conclude mo ulit yung x is equal to y. Kaya nga, you can multiply both sides of an equation by any, maliwanag to ha, non-zero scalar. I think I have to emphasize this. Hindi ka pa pwede kasi mag-multiply ng zero both sides. Kasi when you multiply both sides of an equation by zero, magiging degenerate case siya. Alala niya? parang tinatanggalan mo siya ng karapatang magbigay ng kanyang condition. Parang ito yung ano, pag nag-multiply ka ng both sides by zero, parang ito yung kaklaseng, gusto niyang isama sa swimming, pero ayaw nyo nang pagsalatain, basta kasama ka.

**[20:39]** Huwag ka nang mag-ano-ano dyan. Do you understand? Kasi man yung multiply both sides to zero, nagiging true siya automatically. Parang sabi mo sa friend mo, basta kasama ka at manahimik ka na dyan, wala kang karapatang magbigay ng kondisyon. You understand? Kaya tayo bawal magmultiply ng non-zero. The third operation is the most complicated operation, and this is what you employ when you try to, if you remember this from elementary algebra, this is what you're trying to employ when you're trying to eliminate. Kaya ang untitled na itong slide na ito, di ba? Gaussian elimination. Kasi nag-eliminate tayo ng variable.

**[21:23]** Paano natin ginagawa yun? Di ba? Minumultiply natin yung isang equation by a scalar. Let's say, gusto mong i-eliminate yung x, no? Multiply mo ng negative 2, for example, bago mo i-add sa... third equation. Yung mga ganong klase, no? In general, you are replacing one equation by its sum with a scalar multiple of another. You're multiplying another equation by a certain constant and then add it to the other equation. Naalala nyo ginagawa nyo yun? Do you remember doing this operation? Anyway, ipapakita ko sa inyo ito ng true examples. Huwag kayong mag-alala. According to Gauss, the new linear system that you have obtained by doing any of the following will just be equivalent to the old one. In other words, you do not really change.

**[22:17]** You do not really change the solution set by doing any of the following. And to further illustrate that, talikan natin yung example ko kanina. Ito yung linear system na hindi masyadong aya-aya tignan. For the sake of illustration, I will be Denoting these equations as equation 1, equation 2, and then equation 3, ha? Para may label. Diba yun yung unang step? I-labelan natin yung mga equations. Okay, look at this. Manood muna kayo, na? And then, mamaya, mare-realize din niyo yung algorithm ko.

**[22:58]** Okay? Kasi this is really done or this is really taught by demonstrating and you have to do this by watching first. And then later on, you try to implement it your... own, na? Matututuhan nyo yung algorithm nito by watching me do it first. You understand? Kesa mag, kesa magsalita ako ng formal na algorithm sa simula, di ba? Mahirap yung gano'n, yung we're starting to formal, so maybe let's start on something more concrete. Okay, so if we're going to do it the Gauss way, what I wanted to do first is to interchange. Ang ibig sabihin ko ng symbol na yan, I will interchange equations 1 and 2.

**[23:44]** Bakit yung pinagpalit yun? Kasi alam nyo guys, ang gusto kong mangyari, yung value dito, palaging x. In other words, palaging 1 yung coefficient. Why would I want to put an x there? The reason for doing that is because lahat ng mga excess alim niya. i-eliminate natin. Kasi papatayin ko itong 2x, papatayin ko rin doon itong 3x, gamit yung x. Bakit gamit yung x? Kasi kapag 1 na ito, to eliminate the 2x, it's easy to think of a multiplier. So change mo lang yung sign na ito. I-multiply ko ito sa negative 2. bago ko i-add dito.

**[24:28]** Kung papatayin mo naman yung 3x, imotiply ko to sa negative 3 bago ko i-add doon. Did you understand my intention for doing this? I will be using that x to kill the 2x and the 3x. Question, why would I want that? Remember, diba, I wanted to have that upper triangular form? I do not want to see any x's below that x. Naalala niya? So ang unang step, i-eliminate ko muna yung ibang x's. Halimbawa, how do I eliminate the 2x gamit yung equation 1, imumultiply ko ng negative 2, ia-add ko siya sa equation 2.

**[25:14]** Then it will replace equation 2. So if you do that, negative 2x plus 2x, 0 na to. Negative 2 times 2y negative 4y plus 5y, y na lang siya. Yeah? And then negative 2 times negative 4z, uh, 8 minus 9z, minus z na lang siya, and so on. Okay. Do not worry for now, guys. Do not worry for now kung Ang gusto kong gawin nyo lang ngayon, mag-observe at manood. Kasi alam ninyo, hindi naman ito yung method na ipapagamit ko sa inyo. Okay? I just want you to observe first, to learn the algorithm later on. Nakikita nyo, will make sense.

**[26:04]** But for now, I just want you to sit back and watch. Okay? Observe, observe muna ha? Kung gusto nyo sabayan yung computation, then you may do so. Okay lang. Pero, for now, makakabuting panoorin nyo muna yung algorithm ko. Okay? Next. Okay, x ito. Ito 3x. I wanted to eliminate 3x as well. What do you think should I do? Ganon din. I-multiply ko naman ito ng negative 3 bago i-add sa equation 3, replacing equation 3. So that's the third step. Okay? And you know what will happen if I do that?

**[26:49]** That 3x is now eliminated. As intended. Intention natin yan, na? O ngayon, nakita nyo ba? Nagkaroon ako ng y dito, alright? Nakita nyo nagkaroon ako ng y? Okay, gamit yun. I wanted to have that upper triangular form. Naalala niyo yung form na maganda. I don't want this negative 8y hanging over here, right? So we can use Gauss to eliminate this negative 8y. Now dahil 1 na yung coefficient nung y, madali nang isipin kung anong i-multiply mo dito para ma-eliminate yung negative 8.

**[27:33]** It's just the opposite sign of negative 8, so that's 8. So I'm going to multiply the second equation by 8, add it to the third equation, replacing the third equation. Did you understand that? Do you understand so far? Sundan nyo lang, yung actual mess ng pagkocompute, i-let go nyo muna, okay? Basta, ito yung mga mangyayari. So, ito yung mangyayari. After doing that, may eliminate ni negative 8y, yung third equation turns into 7z equals 7. Now, things are getting nicer. Kasi in third equation, 7z equals 7.

**[28:16]** So, using the second operation of Gauss, you can multiply both sides of the third equation by 1 over 7. Kasi bakit 1 over 7? That will isolate z. and therefore getting the value of z. So nakita nyo na, lumabas na yung form, naka-nais-nais kanina. Nakita nyo yung equivalent. So according to Gauss, lahat ng mga linear systems na ito, ito yung mga binibilugan ko. lahat po sila ay equivalent sa isab-isa. Ibig sabihin, they are solving the same or they are getting the same solution set. So solving one will also solve the rest.

**[28:58]** But of course we stick to this one because this one is easier to solve among the rest. Right?

**[29:10]** Ito na. So as a conclusion, or at this point, we get to conclude that the original linear system is equivalent to the last form. Why would we want this? Because the last form is now solvable by, ang tawag dito ay back substitution. Yung ginagawa natin kanina, yung starting from Z, tapos makukuha mo yung Y from the second equation. Do you realize why is it called back substitution? Kasi pabalik. Starting from the last variable Z, then Y, then X. I-understand? I-gawin natin yung back substitution na yun.

**[29:53]** Well, sabi ng third equation, Z is equal to 1, wala ka nang gagawin dun, meron ka nang value ng Z. From there, i-solve mo yung Y, okay? Second equation tells us it's negative 2 plus Z, so that's negative 2 plus 1 or negative 1. Meron ka na nga yung y. Gamit yung mga values ng y at z na ito, gagamitin mo yung first equation to get the value of x but this time x is if you solve it from the first equation negative 4 minus 2y plus 4z substituting y and z, you get to have the value of 2.

**[30:32]** And therefore, the solution to this linear system is x equals 2, y equals negative 1, and z equals 1. Hindi tatlo ang solution guys ha? Ang solution ay isa lang. yung solution kasi natin by definition is a vector, okay? We only have a unique solution to this linear system. Did you understand? Huh? You understand? Okay, so to illustrate this geometrically, maybe it will help us understand the solution by illustrating through GeoGebra.

**[31:15]** Maybe I should show you what this really means in pictures. I'm trying to show you my entire screen. Hopefully, it does the job.

**[31:33]** Kung medyo maliit yung text, maki-zoom in na lang, ha? So, what I'm going to do, so naka-3D calculator na tayo, right? 3D calculator mode. What I'm going to do is dip sa input bar natin. You just type the equations of the plane one by one. So, for example, 2x plus 5y minus 9z equals negative 10. So, this is the first plane. Ipahin ko lang yung view para mas paganda siya. I mean, mas solid. And I change the background color to black.

**[32:21]** Huwag na, white na lang.

**[32:25]** RTE. Yan yun na. Pasensya nyo na si sir. So that's the first plane. Okay? Yan yung first plane. The second equation is x minus x plus 2y minus 4z. equals negative 4. Oh, hindi masyadong nalalayo, no? Maybe to distinguish one from the other, let me change the color, maybe red. There you go, para hindi makita niya na may difference. parang halos magkapatong sila, nabuti nilang hindi.

**[33:06]** And then, the third plane is 3x minus 2y plus 3z equals 11. At

**[33:17]** papaborito niya yung color na yan. Maka inis. Ano gusto niyo yung color? Green? Red. Ano malayo? Blue. Ayan na lang.

**[33:32]** So may tatlo kang plane, saan sila nag-intersect? Medyo mahirap makita, but dito sila nag-intersect. I-flat nyo lang yung point na 2, negative 1, 1. Hopefully, you can see that point A where they all intersect. Can you see this point A? Can you see that? Dito sa angle na ito, makikita nyo, nag-i-intersect sila doon sa point na yun. So the solution is basically the point where these hyperplanes intersect.

**[34:12]** Okay? Balikan natin to, ha? Sige. Punta lang, mag-concentrate muna tayo dun sa lesson natin.

**[34:26]** Okay? Halika lang sabi ko sa inyo, hindi naman talaga yun yung gagawin ninyo. Now, kasi, first of all, itong method na pinakita ko sa inyo, this can be done in human context. Iksabihin, this is something that humans can understand but maybe a computer will not in its very basic form, no? Kumbaga, This is the solution in human form. We would like to develop an algorithm that a computer also will understand. Paano kaya? Siyempre, AI aside. I mean, kasi ang AI ngayon, marunong na ng context, di ba? Screenshot mo yung linear system yan, iso-solve niya.

**[35:13]** What I mean to say is, hindi yun. Ang sinasabi ko yung basic na computer, yung basic operations ng computer, kung paano ba siya nagko-compute, hindi niya kaya yan unless sabihin mo sa kanya anong meaning ng 2x plus 5y minus 9 equals negative 10, diba? So, what we wanted to do is to use a method that a computer will also understand. And you know what that method is? That method uses matrices. Kasi matrices are something that a computer has already in its functions, no? Marunong nang umunawa ang computer ng It's designed to understand matrices.

**[35:56]** It will not understand the x, the y, the z, no? But it will understand the positions of the numbers in a matrix, right? So what we first do is to represent our linear system as a matrix kasi ita-turn mo siya into something machine-readable. Kasi yung original na form, nakikita nyo, no? Ayan. It's not machine-readable, pero pag nilagay mo siya into a matrix form, it now becomes machine-readable. Right? Ang tawag nyo dito, recall is the augmented matrix of the linear Augmented kasi merong line dito. Parang dalawang matrix ito na pinagdudugtong nyo.

**[36:40]** Yung line naman na yun, guys, it is only there. It's not really there but I am just writing it anyway to separate the left hand side from the right hand side. Naintindihan nyo? Tinatanggal na natin yung mga unknowns, hindi na natin sinusulat. Kasi the positions of the coefficients will tell you kung pang ilang unknown siya. Did you understand? the positions of the scalars alone. Kasi if you look at the operations that we did in the previous slide, hindi naman talaga, I mean, ang trabaho lang ng mga annonce na XYZ are just placeholders.

**[37:20]** Do you agree with me? Hindi naman sila talaga nandun that They play a role in the computing process, right? Naroon roon lang yung XYZ to guide us kung sino yung mga magkakatapat, sino yung i-add, sino yung i-multiply. Did you understand me? So sa totoo lang, huwag na natin guluhin yung memory ng computer, tanggalin na natin yung mga unknown. better to have a matrix instead. So, halimbawa, yung matrix na ay yung linear system na ito will now turn into that matrix at yung magandang linear system na ito, pupaano yan? Walang x, walang y y yung third equation.

**[38:05]** Ang totoo niya, nandyan pa rin si x, nandyan pa rin si y. ang coefficients lang nila, guys, ay zero. Do you understand? Hello? Naintindan nyo ba? Now, of these two matrices, etong matrix na pangalawa yung ating nais. Kasi yung pangalawang matrix na to, is said to be in row echelon form or R-E-F. Kailangan natin bigyan ng tangalan kasi yung, di ba sa, ang term ko lang maganda. Anong ibig sabihin ng maganda? Anong ibig sabihin nyo ng maganda, sir? What does it mean for a linear system to look nice?

**[38:49]** Di ba? syempre dahil nasa matayo, kailangan natin ang definition for that. Ang tawag natin dito sa matrix na ganitong itsura, it is said to be in row echelon form or R-E-F.

**[39:07]** Saan ba nang galing yung term na ito? Ano bang ibig sabihin ng echelon? Yung mga magagaling sa English, can you Can you tell me anong ibig sabihin ng echelon before I continue with the definition? Huh, guys? Can someone please tell me anong unawa nyo sa term na echelon?

**[39:34]** or nagagamit, do you even use this? Just a main position. Yeah, okay. Levels, rank, all of these are correct depending on the usage. But I would like to use what student is saying, yung level na it's actually a parang siyang ano, parang siyang sabihin natin handan or ladder but it's not a physical ladder, rather a ladder of levels or status. For example, pag sinabing military echelon, ito yung ranking ng mga nasa military personnel, ng mga military personnel from private to general. Understand? Private, lieutenant, captain, o mga ganon.

**[40:22]** Sa amin, sa mga ano, sa mga teacher nyo na meron din kami mga echelon. Merong mga Instructor 1, 2, 3, Assistant Prof. 1, 2, 3, 4. They understand ang pinakamataas yung mga professors. Diba? Naintindihan yung ibig kong sabihin ng echelon? So parang it's... Sa corporate naman yan, yung corporate ladder, no? From being an ordinary entry-level staff to becoming a manager, right? May assistant manager pa nga minsan, supervisor, etc. Hanggang maging vice president ka, eventually maging CEO ka. Para naman talaga, no? Do you understand?

**[41:06]** Kung anong siya mo ng echelon? Yung salitang echelon dito, actually, it literally means ladder. Kasi if you can see yung the way the non-zero elements were arranged, no? It's like a falling ladder pattern. parang ladder na pababa. Can you see that? Yan yung echelon form. Sige nga, okay. So, when can we say that a matrix is in row echelon form or REF for short? May tatlong conditions, okay, na kailangang masatisfy. Number one, dapat kung meron ka mang rows of all zeros, puro zeros ang isang row, dapat nasa ilalim yun ng matrix. Hindi ka makakakita ng zero row, tapos sa ilalim niya may non-zero row dapat.

**[41:58]** I understand? Pangalawa, so yun yung mga zero row. Ano namang itsura ng mga non-zero row kapag may mga non-zero element? Dapat, yung first non-zero entry from the left of every non-zero row should be a 1. Nakita nyo? Nakita nyo ba dito sa example na to? Lahat ng non-zero entry from the left of each non-zero row are one. Hindi counted yung mga zero guys, from the left. Naintindihan ba? Nakita nyo one? Ang tawag nyo sa mga one na ito, yun yung mga pivots or pivots or pivots para babasahin. Ako pivots eh.

**[42:44]** I think it's an American thing yung pivot kapag UK ay pivot. Kaya lang, mas masanay ako na pivot eh. Hindi ko alam bakit.

**[42:57]** So, siguro it's either, pivot or pivot. Okay? It's the pivot of the row. Sa bawat non-zero row, dapat may pivot. At ang pivot ay laging 1. Anong ang science behind? Bakit gusto natin 1 yung mga yun? kasi para madaling mag-eliminate. Kapag 1 kasi yun, madaling nang mag-isip ng ipang-multiply para ma-eliminate yung other variable. Did you understand bakit 1 ang choice natin? Sige. Yung pangatlo, Sasabihin ng pangatlo kung paano dapat naka-arrange yung mga 1 na yan. So, syempre hindi pa pwedeng yung mga 1 na yan basta-basta 1 yung first non-zero and three, tapos na. No! Dapat yung mga 1s na yan naka-arrange in a falling ladder pattern. Ano ibig sabihin ng falling ladder?

**[43:56]** Ayan, naka-enumerate. Actually, mas magulo pa yung basahin yung formal eh, kesa yung informal. Tingnan nyo, basahin natin yung formal. Each pivot is in the column to the right of the pivot in the previous row. Diba? Ang gulo. I mean, kapag mabasahin mo siya ng ganyan, yung formal na way, parang ano, yung mata mo iikot, di ba? Kasi nag-i-imagine. Ang ibig sabihin lang nun, tingnan niya ha, balikan ko yung aking example.

**[44:31]** Each pivot is in a column to the right of a pivot. in the previous row. So, in short, wag mo na titignan yung row number 1 kasi may previous row eh. So, dapat start ka na sa pivot sa second row. Nasaan column siya? Okay. Of the previous rows, tingnan mo yung mga pivot. Ito. Yung column ba neto nasa right? Yes. Diba? Itong third na pivot, tingin mo yung column number niya. Tingin mo yung pivot sa mga previous row. Lagi bang nasa kanan? Yes. Understand? Pero ang ibig sabihin lang yan guys, yung mga wands dapat naka-falling ladder pattern.

**[45:18]** Okay? Yan lang ang ibig sabihin ng number 3. Huwag na natin kahirapan yung mga sarili natin, okay? But nevertheless, you know, this is a math subject. We have to write everything precisely or using a precise language. Kaya natin ginagawa ito. So that's what makes a matrix in row echelon form. But you know, in linear algebra, meron pang mas better, mas better eh, meron pang better than the row echelon form. Alam niyo yung better? Ang better ay yung sinatawag natin yung reduced row echelon form, yung RREF. Okay, nakalagay, no? If in addition, so pag narinig niya yung if in addition, what does that mean? Ibig sabihin, if this tree already holds and this thing also holds, sabihin additional condition ito. If this additional condition is true, Then, the matrix A is in reduced row echelon form. Now, what is the additional condition?

**[46:18]** Sabi, sabi, every pivot is the only non-zero entry in its column. Definitely yung example ko kanina, hindi. So, when you look at the pivot, is it the only non-zero entry in its column? Well, yung unang pivot, yes. Pero yung pangalawang pivot, meron kang two sa ibabaw. Kailangan, in its column, dapat, ano, siya na yung nag-iisang, ah, siya lang nag-iisang non-zero entry. and also on the third column.

**[46:57]** So, this is in REF but not in RREF. This is only in row echelon form but not reduced. Ano bang itsura ng isang reduced row echelon form, guys? Let me show you one example. Halimbawa, kung ganong size, same size, dapat kapag 1 yan, dapat 0 na ito. Kung 1 ito, dapat 0 din yung mga kasama niya. Tapos, kung 1 ito, dapat 0 yung mga kasama niya. Do you understand? Tapos, ito kahit ano, halimbawa, 1, 2, 3, kunwari lang.

**[47:38]** Pag kasi ganyan na yung echelon form, makikita nyo, if this column is the column of x, this is y, this is z, makikita ninyo, the linear system is already solved. Wala ka nang gagawin kahit na back substitution. Kaya sa linear algebra, mas gusto natin yung naka RREF. You have already solved the linear system. No need for back substitution. No need for this additional step. Did you understand? Kaya gusto natin yung reduced. Hopefully, naintindihan ninyo yung aking definition.

**[48:21]** So of these two, ito yung ating preference talaga. Yun nga lang, you know, it takes us more time to obtain this than this. Nevertheless, At least, hindi ka na kailangan mag-back substitution. Pangalawa yung back substitution, ang hirap pa i-program nun, di ba? Mahirapan ka pang mag-isip. Bakit sa umpisa pa lang, di isama mo na hanggang RREF para isang programan lang? They understand the point? And also, I have... a mathematical reason why doing an RREF is a lot better. Mamaya papaliwanag ko sa inyo. But, for now, I have five different matrices here.

**[49:06]** Wala muna tayong linear system. Kalimutan nyo muna yung mga linear systems. Okay? So, mga plane na matrices lang sila. Ang gagawin natin dito, i-identify natin if each one is in REF, at doon sa mga naka-REF, i-identify natin sino ang naka-RREF. Kasi remember, bago ka ma-RREF, dapat REF ka muna. You understand? Hello? Sige, gawin natin. Let's look at the matrix A. Is it in R, E, F? Okay, nakatandaan yung tatlong condition, so I will enumerate one by one.

**[49:48]** A, meron bang zero row si A? Meron, no? Sa ba ay nasa ilalim? Nasa ilalim ba sila? O isa lang naman? Nasa ilalim ba siya? Yes po. So, satisfied yung condition number one. Tignan mo ngayon yung mga non-zero row. Ito yung tatlong non-zero row. Yung first non-zero entry ba from the left are all ones? Yes, yes, yes. So satisfied yung condition number two. Are these ones in the falling ladder pattern? Yes po. Hindi naman kailangan pantay-pantay na one step lang. Ang importante, column to the right of the previous rows.

**[50:32]** previous five votes. Naintindihan ninyo, tulad na ito, falling ladder pa rin ito. Idrawin nyo palagi sa isip nyo ito kasi mahalaga siya. Ay, mali yun.

**[50:49]** Ito yung ladder natin. Did you understand? Medyo uneven lang yung mga steps. Okay. nawala yung aking, ano, na iPad. So meaning to say, alam nyo na, yung internet ko'y bumabagal, taglit lang, and you'll have to reconnect.

**[51:17]** Taglit ha?

**[51:28]** Diyan lang kayo, huwag kayang ales, please.

**[51:42]** Um, nire-restrict ko lang yung... software. Pag nangyayari kasi ito, nire-restart siya talaga. Dapat.

**[52:00]** There you go. I guess I'm back. Okay? I am back, na? So, ito lang ngayon yung mga one and it's now in the falling ladder pattern. So, we can say that A is in... REF. Tignan nyo yung table dito sa ilalim, nakikita nyo yung table, nilagyan ko ng check yung REF, so i-sabihin ko niya, naka-REF si A. Question, so naka-REF na si A, is it in RREF? Anong i-sabi nung isit in RREF? So, naka-REF siya. I-check mo na lang kung yung yung yung mga pivots nyo ba yung natatangin ng zero entry in their columns. So, tingnan nyo ito.

**[52:47]** Zeros, okay? Zeros. Ito. zeros. Okay, very good. So, si AI, naka-RREF, fortunately. Alright? Guys, naintindihan ba so far? How about B? Tingnan natin si B. Si B. Alright, may zero row ba si B? Yes? nasa ilalim ba siya? Opo, so satisfied yung condition number one. Of the non-zero rows, are the first non-zero entry from the left ones? Yes, they are pivots, right? So, are they in the falling ladder pattern?

**[53:32]** Yes, so matrix B is in? R-R-E-F. Question, is it in R-R-E-F? Yes or no? Guys, is B in R-R-E-F?

**[53:59]** Sabi ni student, yes. Sabi ni student, no. Sabi ni student, no. Mas maraming no. Okay, bakit no? Bakit? No? Would like to volunteer sa answer? May negative 2, okay. Dahil sa negative 2. I think what you mean to say is when you look at the pivot on the second row, so this is the pivot on the second row, right? There is an asungot here, no? May negative 2. sa column nung pivot na yan. Ang gusto lang natin, nung zeros lang ang kasama niya. Ang mga pivots na naka-RREF, mga seloso yan, gusto na yung attention na sa kanila lang, mga main character sila, na? Kapag naka-RREF, ayaw nila ng may ibang umaagaw ng spotlight nila. Gusto na sila lagi bida, di ba?

**[54:48]** So, although matrix B is in REF, it is not in RREF. Okay, guys? Okay, let's now turn our attention to the matrix C. Is the matrix in REF? Let's check one by one. Meron bang zero row? Yes. Kaya lang, ang problema dito, may non-zero row sa ilalim niya, so it's not at the bottom. Na? Nakita nyo, yung zero row na to, it's not at the bottom, top pala siya, charot, hindi versa siya na sa gitna.

**[55:32]** Nakita nyo, wala siya sa bottom part. So, unang condition pa lang, no na. So, no na. Huwag nyo lang i-check yung ibang conditions pag may isang condition ay nag-fail to hold na. At dahil hindi na ito naka-RREF, may chance abang maging REF siya? Of course not. Yung iba, minsan panglito ko ganito. Panglito ko ganito. Minsan, yun ang papalito ko sa examen ito. Diba? Ito, 1-0-0. Tinanong ko, naka-REF ba? Hindi raw, kasi nga may zero row sa second row, tapos in third row ay non-zero. Okay, tinanong ko, naka-RREF ba siya?

**[56:17]** Biglang ang sagot yes, kasi nga yung mga one ay, antag neto, puro zero ang kasama. No, mali po yun. Kasi bago ka mapunta sa RREF, dapat naka-REF ka muna. Kaya once na X na ang REF, tandaan nyo, X na rin automatic ang RREF. Did you understand me? Naintindihan ba yun? Pre-requisite. ang REF ng RREF. Kaya nga may REF sa loob ng RREF, guys, ha? Huwag kayong mako-confuse. Letter D. Is it in REF? Let's check one by one.

**[57:02]** Does it have a zero row? Yes. It is in the third row. Okay. Okay yun? Taglit lang.

**[57:13]** Okay, let's look at the first non-zero entry from the left. Ito one, oops, negative one. Pwede ba yung negative one? Negative one lang naman sir eh. Pwede na ba yun? Hindi na kasi by definition it has to be 1. Ang pivot natin lagging, 1. So yeah, violated yung condition number 2, so no, therefore that is also no. Okay? Last but not the least, do we have a 0 row? Wala naman, so wala kang problema sa condition number 1. Number 2. First non-zero entry from the left? 1, 1, 1. Okay. Satisfied yung condition 2.

**[57:58]** Is it in the falling ladder pattern?

**[58:03]** No. Meron bang hagdana na gano'n ang ginagawa? Wait lang, wala na naman yung aking slide.

**[58:17]** Ah, kainis. wait lang ha, tension ha,

**[58:32]** ayan, can you see it again?

**[58:37]** Medyo bumibitiw. Itong hirap kapag wireless yung connection minsan bumibitiw. So, hindi naka-falling ladder pattern. Kapag ang hagdanan nyo sa bahay ganito itsura, ewan ko na lang, di ba? May hagdanan mga ganyang itsura, meron. Ito yung taguan ng sapat, ng chinelas, di ba? Dito nyo tingalagay yung mga chinelas nyo. Sa hakbang kanapaganan. Sarap. Hindi siya standard na hagdanan, kaya... It's not in REF. Okay? Syempre, dahil hindi na naka-REF yan, hindi na siya naka-RREF. Huwag nyo nang abalahin yung sarili ninyo.

**[59:22]** Nakita nyo, no? Lahat ng mga kasama ng 1 ay 0, so you may think na naka-RREF siya. No. Pre-requisite po ang REF. So ngayon, marunong na kayong magspot ng REF at RREF. Tuturuan ko na kayo paano i-tra-translate yung Gaussian elimination operations, naalamin yung tatlong operations natin kanina, inagsaswap ka ng dalawang equation, nag-multiply ka by a non-zero scalar, or nag-a-add ka ng equation to a multiple of the other. Paano natin yun i-convert into matrix operations?

**[1:00:07]** So, ito na yung kinatawag nating elementary row operations. Okay? We call this the elementary row operations. Tatlo lang din yan, kasi tatlo lang yung operations na allowed ni Gauss. Yung operation number one, or yung type one, Ito yung row interchange operation. Kasi pag kayo'y nagpapalit ng dalawang equations in a linear system, ang nangyayari yung corresponding matrix nun, nagtapalit lang yung dalawang row. So, pag pinagpalit niyo yung row i tsaka row j, ganito yung notation. Para hindi natin sinusulat ito ng mahaba, di ba ang haba kung isusulat nyo to, right?

**[1:00:49]** Si sir, meron akong class notations, okay? Itong notations nito are only in our class. You may not find this being used in other books. Pag nagbukas kayo ng ibang libro, maaaring iba yung notation. Kaya nga nang sabi ko sa inyo kanina, nung nag-aaral kasi ako, mahilig ako gumawa ng sarili kong mga notations para mas madali para sa akin. Alala niya yung matrix multiplication ko, diba? maaaring hindi nyo makita yun sa ibang libro, kagaya na itong mga annotations na ito. Instead of writing this, we will abbreviate that by EIJ. Kaya E kasi para to remind you that this is an elementary row.

**[1:01:35]** operation. Kapag nakakita kayo ng EIJ or E23, ang ibig sabihin nun, inuutosan ko kayong pagpalitin yung row 2 tsaka row 3. You understand the notation? Type 1, row interchange. Hello guys. Okay? utos yan, command. Ganito yan. Ang purpose din eto guys, para pag nagre-review kayo mag-isa, hindi man ako nagsasalita eh. Diba? Nakita nyo, nire-review nyo yung notes ninyo. Nakita nyo kung anong ginawa ko dun. kasi nakasulat o nakarecord kung anong row ang pinagpalit ko. Ay, pinagpalit ni sir yung row 2 tsaka row 3.

**[1:02:17]** So, hindi nang i-sabihin nun. Okay? Yung type 2 naman, when you multiply an equation by a non-zero scalar, ang ginagawa nyo, yung isang row, minumultiply nyo by a scalar. So, for example, if the ith row or the row i gets multiplied by a scalar alpha where alpha is not zero, by the way, alpha is not zero here, ha? We will denote that operation by the following symbol. Very efficient yung notation na ito, no? Ang nakikita nyo lang dyan yung mga kailangan nyong makita. For example, ang sabihin ng I, yun yung row kung ano yung imumultiply nyo by alpha. Multiplier yung alpha. Naintindihan?

**[1:03:01]** Hello? You understand? Yung pangatlo, which is the most complicated of the three, but not really kapag... tumagal, masasanay kayo. Meron kang tatlong parameters, i, j, and alpha. Ano yung i, j, and alpha? Isabi ng i, yun yung row na papalitan mo. Yung j, dun mo imultiply yung alpha bago mo i-add dun sa lumang row. Did you understand? So, yung Eij alpha, papalitan mo yung row i ng ano? Row i plus alpha times row j. Sa row j mo, minumultiply yung alpha. So, umpisa, medyo malilito kayo, promise?

**[1:03:47]** Pero... Kung ginagawa nyo or kung nagre-review kayo, sinusulat nyo ito by hand, the only way to learn this guys is to actually do this by hand. Promise. Hindi nyo ito matututuhan ng, I mean, yung ituturo ko sa inyong algorithm, hindi nyo matutuhan hanggang hindi nyo ginagawa by hand. Manwala kayo sa akin, kung ang study habit nyo ay manood lang sa mga recorded videos or manood na mga videos sa internet, I'm sorry to say, mahihirapan kayong matandaan yung algorithm. na tinutukoy ko, yung Goss-Jordan method na tinatawag nyo sir.

**[1:04:29]** Okay? Kaya ang aking pakiusap sa inyo, if you have time, maraming mga materials may binigay ako sa inyo na yung link sa mga other textbooks. You try the exercises, you do it on your own. Patignan nyo nyo. Pwede nyo namang gawing, ano eh, study partner ang, ano eh, ang Gemini, ang ChatGPT. Sa ganyan paraan nyo dapat sila ginagamit, diba? Alimbawa, you can ask the AI to finally check if my work is correct. Which part did I get? the answer wrong, no? Which part of the answer is wrong? Yung ganon, sa ganong paraan nyo mapapakinabangan ng AI. Di ba? It's a good use of AI kasi you're learning.

**[1:05:18]** Hindi, hindi, hindi nyo ginagamit yung AI just to comply. Nakikita niyo yung difference, no? Difference. Ito ay kasama sa aming AI education, no? Kasi we have to... AI can be dangerous especially sa mga students kasi instant gratification yun eh. Diba? And instant gratification is, you know, it's not very good sa mga children. And if you think that you are not children, you are wrong. You are still children to me.

**[1:05:58]** hindi maganda ang instant gratification, lalo ngayon where everything is almost instant, no? Try nyo pa rin, kasi hindi kayo matututo pag everything is instantly available. Okay? Meron tayong terminology, yung row equivalent, no? Ito yung parang kahawig ng equivalent na linear system kanina. Kaya lang dito, may salitang row equivalent kasi I want to emphasize that we're working on rows not on columns, okay? We say that matrix A is row equivalent to B.

**[1:06:41]** This is how we normally would write that. If B can be obtained from A by a finite sequence of elementary row operations. Ibig sabihin, kung makukuha mo lang si B gamit yung mga row operations na ito from A by applying it to A, then A and B are row equivalent. Ganito yung notation. In particular, pag gumawa ka ng isang operation na E, in-apply mo sa A, lumabas si B. Ganito ko siya karaniwang sinusulat. Nilalagyan ko ng arrow, nilalagyan ko sa taas ng arrow yung operation na ginamit ko. For you to know, kapag kayo nagre-review na, ano ba yung ginawa ni sir to obtain B from A? Ah, this is what he did. Minultiply niya yung row 3 by 1 third.

**[1:07:32]** Ayong kundyanin niya? Papakita ko sa inyo yung actual. Halimbawa, look at the matrices on the left. So, anong meaning ng mga arrows na yan? Anong mga symbols na yun na nasa taas ng arrows? Ibig sabihin nyan, inuutosan ko kayong gawin yung mga sumusunod na operation. Halimbawa, makikita nyo sa unang example, E12. So, I am asking you to row interchange. row 1 and row 2. Do you understand? Understand that, guys? Madali lang ito. Yung type 1 ang pinakamadaling gawin sa lahat. So, yung second row, ilalagay mo lang sa first row. Yung first row, ilalagay mo sa second row.

**[1:08:16]** Finish na. Lalo na kadali. Medyo nakakalito lang ang row interchange, guys, pag malaki yung matrix ninyo, especially when it has a large number of rows. But nevertheless, padali lang naman siyang gawin. Okay? Next, anong meaning ng E2, parentheses, negative 3? Type 2 ito. Kasi pag isa lang yung subscript, i-sabihin nyo yung type 2. I-sabihin nyo yung second row, i-multiply nyo lang by negative 3. So, what you're after is, yung first row ay hindi naman talaga gagalaw, hindi magbabago.

**[1:08:59]** I-multiply nyo lang ng negative 3 yung second row. So, negative 3 times 3. negative 9, negative 3 times 4, negative 12, negative 3 times 0 is still 0. Do you understand? Right now, guys, so far? Siguro dito kayo malilito sa pangatlab. Marami nagkakamali dito sa pangatlab at... nasasanay naman, based on experience, after a month or so, bihasang-biyasaan yung mga students ko. Kasi alam nyo, itong pag-RREF guys, maniwala kayo't hindi, gagawin na natin ito araw-araw ng buhay natin hanggang matapos ang semester.

**[1:09:42]** Kasi alam nyo, walang problem sa linear algebra ang hindi masusolusyonan ng RREF. Kaya nga, pakiramdam ko kung meron mang lesson ang pinakaimportante sa lahat itong araw na to. Kasi parang Either you know how to do RREF or not. Kapag hindi ka marunong ng RREF, malamang sa malamang yung mga susunod na problems sa linear algebra na isasolve natin, hindi mo magagawa. Kasi almost lahat ng problems ng linear algebra relies on your ability to reduce into RREF. Okay?

**[1:10:24]** Now, ano to? Yung unang subscript, 2. Ibig sabihin nyo, yung second row lang ang magbabago. Yun yung hint dun ha. So in short, yung first row, huwag nyo nang galawin. I-re-write nyo na lang yung first row. Kaya ako lang naman nilalakihan ng ganito, kasi ipapakita sa inyo kung paano ko gagawin yung second row, no? Yung second row, siya pa rin, 3, 4, 0. Except, ia-add mo ngayon yung negative 3, times the first row. So sa first row, yung multiply mo yung negative 3, so it's actually minus 3 times 1, minus 3 times 2, minus 3 times negative 1.

**[1:11:11]** Did you understand?

**[1:11:18]** O ganito, ang ibig sabihin lang po nyan guys, yung negative 3, yung multiply mo sa first row, i-add mo sa second row. Lalagay mo sa second row. Paganan ang baso dyan, pabalik, no? Negative 3 times first row plus row 2. Tapos lalagay mo yung sagot sa row 2. Okay? Entindihan ba? Pabalik. I-multiply yung negative 3 sa first row, a-add mo sa second row. Kaya lang, sinahaba ko lang dito. Kaya, ang sagot, 0, negative 2, positive 3. So nakita nyo, by doing this operation, anong nagawa natin?

**[1:12:03]** By doing this operation, we were able to eliminate the three gamit yung pivot na one. Naging zero na siya yan. Nice na?

**[1:12:16]** Ang sinasabi ni sir, halimbawa yung matrix na ito, isipin mo linear system. yung linear system yan, ang itsura nung nasa kaliwa ay ganito. By doing that single step, you have turned your linear system into x plus 2y equals negative 1, negative 2y equals 3.

**[1:12:41]** Nahintindihanin niya? So ngayon, maganda na! practically solved na yung pangalawa, di ba? Iyon yung sinasabi natin. The reason why we're doing elementary row operation. Ito, challenge. Naku, malaki to. Sabi, find the matrix in RREF which is row equivalent to the following matrix. So, anong ibig sabihin ko nyan? Ang ibig sabihin ko nyan, guys, gagamit ka ng mga elementary row operations, yung tatlo lang, wala kayo ibang pwedeng gawin, hindi nyo pwedeng pilitin. Hindi pa pwedeng RREF by Erasure. Halimbawa gusto mong ma-eliminate ang binura mo, hindi pwede yun.

**[1:13:26]** Ang pwede lang yung tatlong operation ni Gauss. Yung Type 1, Type 2, at Type 3. You are only allowed to use that. Aside from those, wala nang ibang pwedeng gamitin, especially erasure. Minsan ay inis, hindi ma-eliminate yung five. Ang ginawa, binura, ginawang zero. O di ba ang galim? Elimination by erasure. Oo nga naman. Siyempre mali yun. Kasi when you just erase, you're not... Really, you're not really working on an equivalent linear system. Denyaya mo, no? Medyo mali yun. Okay.

**[1:14:09]** Tandaan nyo, ang unang step palagi is to create a pivot over here. Kasi you will use that pivot to eliminate the things under it. Kaya lang makita nyo, 0 to, it's not a pivot. If I want a 1 here, nahanap ako ng 1 sa ilalim para makipagpalit. Hindihan niya? For example, I can first do E13. Ang isabi ng E13, Interchange, row 1, and row 3. So yung row 3 mo ngayon, narinito na, o minsan, guys, alam nyo pag tinatamad si sir, hindi ko nagina-drawing itong bracket ng matrix kasi nakakadagdag pa siya sa ano?

**[1:14:53]** Sa alalahanin. Hindi ka pa timing to say. Hindi ko na sinusulat yung bracket para makatipid sa space, at saka sa time.

**[1:15:08]** Naintindihan, guys? Eh, ang tanong ni Sir, Sir, paano kapag wala kang 1 dito? At saya, ang meron ka dito, 14. O, diburahin natin yung 4. Sarap, ganun na yan. Paano kapag walang 1 dyan? Anong gagawin natin? Let's say, 5 ito. Well, for the meantime, you can first interchange with the second row. So, wala kang choice eh. 2 dito, tapos 0 na yun. Ang gagawin mo para magka-1, gagamit ka ng type 2, mumultiply mo ng 1 half. yung buong first row after. Kasi by doing that, forced ka na magkaroon ng one.

**[1:15:51]** Naintindihan nyo? Paano kapag walang one?

**[1:15:57]** Alam nyo guys, kinuturo ko na sa inyong algorithm without telling you that I'm teaching you the algorithm already. Okay? So later on, I will ask you to... write a program about this. Sige. Ito na, may 5 vote na tayo sa first row. But it's not yet a 5 vote kasi guys, meron pa mga asungot sa ilalim niya eh, di ba? You want them be eliminated. So meaning to say, I want to kill that 2, I want to kill that 3. So, kailangan kong mag-apply ng dalawang type 3 operations to kill that 2 and to kill that 3. Parang ang pangit nung kill. Anyway, okay lang yung naiintigyan nyo naman, no?

**[1:16:44]** So, to eliminate the 2, nasa ang row ba ang papatayin? sa second row. Nasaan yung barrel natin? Yung barrel natin yung pivot? Nasa first row. Anong opposite sign ng 2? Negative 2. Kaya, opposite sign, kasi pag minultiply mo ito sa first row, in-add mo sa 2, mag-cancel yun. Nakuha niya? So, para hindi tayo maka maubusan ng oras, para mas mabilis, isasabay ko nang patayin kasi nasa same column lang naman sila, no? Isasabay ko nang patayin yung 3 doon sa 4th row gamit yung 5 votes sa 1st row by multiplying negative 3.

**[1:17:30]** Ang kong ganyan yung operations na yun, hindi nakasya kayo, nilagay ko sa ilalim lang, ha?

**[1:17:39]** Okay. So, umpisa, ganito tayo kabagal, but later on, you know, tayo'y bibilis ng bipilis, okay? Okay. 1, 1, 1, 0, nothing will really change here. Ito na, ito na yung difficulty. Kasi alam natin magsisiro to, kasi that's the purpose, kaya nga natin sinulat yun. Pero ang difficulty ay yung mga susunod na elements, kasi ang gagawin mo, negative 2 times 1 plus 2. Ganun yun, di ba? Negative 2 times 1 plus 2. Negative 2 plus 2, oh, 0 rin. Okay. Negative 2 times 1, plus 0, negative 2.

**[1:18:21]** Negative 2 times 0, plus 6, 6, kasi times 0 yun. The third row will not change at all, okay? Ito na, fourth row. Mamamatay yun kasi yun yung intention ng second operation na yun eh. So, ma-multiply yung negative 3 dito ulit, pa-add ko dun. Of course, that will be 0 as well. Negative 3 times 1 plus 1, negative 2. Negative 3 times 0 plus 6 positive 3. Nakikita nyo na ba yung danger na nakaamba?

**[1:19:05]** Isang number lang ang magkamali kayo. Mali na yung mga susunod na steps. Nakikita nyo yung danger? No? especially during exams, alam nyo naman, diba? You have to really be careful. But don't worry kasi, you know, during exams, I know the time pressure, I understand the time pressure, I know the, uh, yeah. medyo mabilisan yung mga bagay kapag long exams. So, I actually Write the problems carefully. Tinitignan ko yung mga steps, yung number of operations na kailangan nyong gawin. Tinoconsider ko yun when I construct an exam.

**[1:19:54]** Kaya nga ayokong ayokong gumagawa ng special exam kasi hindi ang mga long exams ko ay pinag-iisipan kong mabuti. No? bago ko i-deploy. Inuulit-ulit kong sagutan, on my own, sinacheck ko yung mga pagdadaanan ninyo in order to get to the answer. I consider all of those. Paraniwan, dinidesign ko yung mga problems to

**[1:20:25]** avoid long computations, kasi you know, bobo nga ako dun eh, diba? Ba't ka naman ipapagawa sa inyo yun eh, kahit ako hirap na hirap, diba? Pag maraming mga operations. I normally select the problem so that you will not spend most of your time in one problem only. You know what I mean to say? Minsan, tatlong step nga lang, naka-RREF na.

**[1:20:50]** I really do that. I mean, I design the problems to be that way. Kung paano ko siya ginagawa, you can just think about it, kung paano yung ginagawa.

**[1:21:06]** Ayan, tignan nyo. Sir, bakit po naging 3 yung last number sa bottom row? Mali, no? Oo. Kasi bobo, tanga-tanga ko eh. 0 nga pala ito. Ang nasa isip ko, 1. So, negative 3 times 0 is 0 plus 6. Dapat ito ay 6 pa rin. Thank you.

**[1:21:32]** Ayun yung sinasabing sa inyo, ako nga nagkakamali eh. Kaya nga as much as possible, alam nyo, hint, sa exam, pag nakikita nyo medyo lumalaki yung mga number mo, naging 18 plus 35 times 7. Pag mga naging gano'n na, most likely may mali kayong ginagawa. Kaya nga nang sabi ko sa inyo, dinidesign ko yung mga exam problems so that the numbers will not get too big, you will not get a lot of fractions kung meron man, kasi bobo ko dun eh. Kaya kapag nakita nyo yung sagot nyo, yung solution nyo, medyo nagiging out of hand na yung mga numbers. Most likely may mali kayong ginawa.

**[1:22:17]** Nagigets nyo? Naintindihan nyo?

**[1:22:25]** Okay. Next step. We want the first non-zero entry from the left to be 1's right. Kaya lang ito negative 2 eh. Ito na yung negative 2. So maybe we can multiply the second row by negative 1 half, the fourth row by negative 1 half also, para maging 1 sila, diba? So magiging 1 to, ito negative 3 na.

**[1:22:59]** Parehas lang pala, no? Kaya lang, when you look at the arrangement of the pivots, naku, may lalagyan ng sapatos, no? Entendahin nyo, may lalagyan ng sapatos dito, bawal yan. So, i-rearrange natin yung rows, gamit ang row interchange. So for example, I can... Interchange, row 2 and row 3.

**[1:23:27]** Nakukuha nyo yung notations ko, guys. Naintindihan nyo na. Okay? Sige. 1, 1, 1, 0, 0, 1, 1, 1, 0, 0, 1, negative 3. Ayan. Mas mukhang ano na to. Makatotohanan na to. Diba? Yup. Now, hinaw-identify, kasi pipivot ka na sa first row eh. Pivot na tong maliwanag. Hinaw-identify the pivot on the second row. Ito na siya. Dahil gusto muna ka RREF. ayaw mong may asungot doon, so you have to eliminate the one.

**[1:24:07]** Yung asterisk, pag nakita nyo sa solution sheet nyo, ay sa review materials nyo yung star, isabi nyan, I wanted to eliminate that, para alam nyo kung bakit yung susunod na operation nyo naging decision ko. Halimbawa, On which row is that one with a star is found? It's in the first row. Kapatayin ko siya gamit yung aling pivot, yung katapat niya sa column niya, which is in the second row. Anong mumultiply ko doon sa pivot? Negative 1 kasi opposite sign ng star. Puha!

**[1:24:49]** Okay na.

**[1:24:53]** Multiply. So wala naman talagang ibang gagalaw dyan, kundi yung first row. Yung second row, pababa, hindi yung gagalaw.

**[1:25:07]** Okay? Sulat mo na, kasi hindi naman siya gagalaw. So yung first row, anong gagawin natin? Negative 1 times 0. Sa second row magmumultiply, guys. Second row kasi 2 yun. Plus 1. Kita nyo, 1 lang din niya kasi 0 na yun. Kukopihin mo na lang whatever is above the 0. And then this will become 0 kasi that's the intention. Okay? Negative 1 times 1 plus 1. Oops, 0 na naman siya. Nice! Negative 1 times 1 plus 0, that should be negative 1. Did you follow?

**[1:25:55]** Did you follow? Anyway, you can always get back now. Kasi nakita nyo, recorded lahat ng steps. Yun yung maganda sa notations na to. The steps are all recorded. Kung baga kung hindi kayo nakasunod, you can always, um, ang tag neto, go back and review. Kaya lang, kaya gusto ko pa rin nasabay kayong nag-aaral sa akin as I talk. Kasi alam nyo, yung pagde-decision ba kung anong operation yung gagawin na susunod, you have to learn it also. Kasi alam nyo, yung ganitong setup natin, There is an impression na dahil nakakasunod or nasusundan nyo yung ginagawa nyo, you thought na kayo nyo na siyang gawin mag-isa. Alam nyo ba, based on my personal observation, ang difficulty talaga ng students is not really performing the RREF but rather, yung selecting kung anong susunod na gagawing step, no?

**[1:26:57]** Kasi nasanay kayo na nasa feeling ko kapag online class, di ba? Ang nagiging problema pag mag-isa na. Kaya nga I am asking you to practice.

**[1:27:13]** Diba? Take the opportunity na merong AI to be your review partner. Okay? Ituro nyo sa AI yung notations natin para matutuhan niya, yung E13. Kayang-kayang matutuhan niya ng AI. Diba? Hmm. Next. So check na tayo dito. Check na tayo dito. We now want a pivot on the third row. Of course, this has to be it. Pababa tayo ng pababa ha? We started with the first row, then now we're settled on the first two rows, the next step, the next natural step sa third row. Ito na yung target pivot natin.

**[1:27:53]** Kaya lang, dahil na RREF ang gusto natin, oops, dalawa ang papatayin natin sa tapat niya, si 1 tsaka sa negative 1. So you are expecting to do two type 3 operations. Sige nga, can you tell me the two type 3 operations? type it in the chat box so I know that you're learning how to write a correct operation. Sige, to eliminate the one above and to eliminate the one below, what are the two operations should I do? Can you type it in the chat box please? I will wait for your answers.

**[1:28:36]** para ma-check ko kung nagigats nyo yung pag-code ng mga operations. Ulit, yung first subscript, kung nasa nyo papatayin, yung second subscript, kung nasaan yung pivot, okay? Of course, yung nasa parentheses, yung multiplier. Ayan, yung mga sagot na sa chat box. Okay? I can see na yung mga scalars ay negative 1 sa loob ng parenthesis. Of course, kasi 1 yung mga papatayan, ano? It's now a matter of checking if correct yung indices ng mga i. Okay, tingnan natin. Okay, it looks like you are all correct.

**[1:29:21]** So, alimbawa, to eliminate this one, it's in the second row, so E2, the pivot on the third, opposite sign of the star is negative 1, okay? To eliminate this one, it's in the fourth row, the pivot on the third, opposite sign is negative 1. Yeah, so you are all correct. Thank you for your participation. Let's now do the actual computation. That's 1, 0, 0, negative 1. Okay, ito na. Negative 1, saan mo multiply? So third row.

**[1:30:02]** plus, plus, tatandaan ninyo, pag zeros na yung nasa unahan, kung ano yung nasa patapat, kukopyahin nyo na lang, kasi zero na yun, kahit ano yung multiply nyo, wala na, baliwala na. So actually, mula dito hanggang dito, hindi na magbabago yan. kukopyahin mo na lang siya literally. Okay? Kasi ito magsisiro, kasi yun yung intention. Okay? Naintindihan niyo ba? Yan yung intention, magsisiro yun. And then, ito lang yung kukumpitin mo talaga dyan, negative 1 times negative 3 plus 1. So, that's 3 plus 1. I think this is 4.

**[1:30:47]** Did I do it correctly? Ano ba yung pagkakagawa ko? Okay, let's move on to the fourth row. Nakita nyo ba 0, 0 na ito? So, yung mga nandito, kukopihin nyo lang yan literally. Ito pala, dahil nandyan yung pivot, hindi namang gagalaw yan. eto kukopihin nyo lang, eto yung zero nyo, kasi yun yung intention. Negative one times negative three plus negative three. So that's three plus negative three, that's zero. Alright, so nakita nyo, now there is a zero row. Ang maganda naman, nasa ilalim na siya, okay? Maganda pati, kompleto na yung pivot ng mga non-zero row at nasa falling ladder pattern.

**[1:31:38]** At the same time, walang ibang kasama. Bida-bida yung mga pivots natin in their respective columns. So, we're done. Nakuha niya. So the algorithm stops and we are done. So therefore, 1

**[1:32:01]** 0 0, negative 1, 0 1, 0 4, 0 0 1, negative 3, 0 0 0 0 is a matrix in RREF which is equivalent to the given, row equivalent to the given

**[1:32:27]** matrix. Which understand guys? Naintindihan niya? Alam niyo mo what you just did by doing all of this? Parang ka nag-solve ng linear system, hindi nyo lang alam. Imaginin ninyo x, y, z to. Imaginin nyo x, y, z yan. So yung linear system ninyo parang y plus z equals 1, 2x plus 2y equals 6, x plus y plus z. x equals 0, 3x plus 3y plus 1 equals 6, diba? But then, in the end, ang nangyari, x is negative 1, y is 4, z is negative 3. yung nasa ilalim, degenerate yun. Lagi namang true yun eh.

**[1:33:19]** So you can just drop it out. Nakuha, you were actually able to solve a linear system. Kaya, pag ganito, ayaw ng mga estudyante gawin eh no? Pero pag sa Facebook, ano yan? Yung apple plus orange plus orange equals 9. Mga ganun, ang sisipag nyo sumagot, mga hayop kayo eh, no? Pag nasa klase na, ginawa lang XYZ, ayaw na.

**[1:33:50]** nakikita nyo daw sa Facebook yung mga ganong means. May mga apple plus orange plus orange equals 39, yung mga ganan. O, diba? Linear system lang yun eh.

**[1:34:01]** O, diba? So, here's the fact. Lahat ng matrix talaga ay marereduce mo to some matrix in R. That's a fact, no? Ang reason pati, kaya gusto ni sir na naka-RREF, kaya gusto ko RREF, kasi isang matrix lang in RREF ang meron that is row equivalent to your given matrix. What I mean to say is, let's say ganito, Let's say, I ask everyone in class, sabi ko, sigo nga, find a matrix in REF equivalent to this. Pag REF lang ang hiningi ko, iba-ibang studyante, possible na iba-iba ng sagot at pare-parehas kayong tama.

**[1:34:47]** Okay? Isang advantage when I ask us to When I ask everyone to give me a matrix in RREF, kasi isa lang yung lalabas na sagot, wala na akong ibang hahanaping sagot. Kasi when you look at the RREF, mapipilitang maging yun eh, kasi sinisiro mo yung nasa ilalim at ibabaw nung 5 watts. Pag RREF kasi, Pwede kang may 2 dito, pwede kang may negative 1. Malaming possible answers ay nilihalin nyo.

**[1:35:21]** Because of that form, napipilitang magiging unique ang matrix na naka RREF. Kaya nga minsan sinasabi ko, find the RREF, ginagamit yung article na the. kasi isa lang ang RREF. Although marami kang possible na REF, iisa lang ang RREF. Kaya nga in-underlinean ko dito, nakita nyo, unique, no? And the idea is that, kaya natin ginagawa lahat ito, kasi kapag si A and B yung mga augmented matrices, two linear systems, then at kapag si A ay row equivalent to B, sabihin yung dalawang linear systems mo are equivalent.

**[1:36:03]** And we now have developed the so-called the Gauss-Jordan method. Anong Gauss-Jordan method? So, ang ginagawa natin sa Gauss-Jordan method, ito na-turn natin into a matrix yung linear system. So, that's the augmented matrix, right? So, ang ginagawa natin, humaharap ka ng matrix B in RREF that is row equivalent to the original matrix, okay? Ito na nga yung sinasabi natin yung reduction to RREF, yung step 2. Ito yung mahabang step, yung step 2. Pag marunong na kayo noon, i-re-write nyo lang ulit si B as a linear system, use back substitution if needed. Kung hindi na, o di hindi na.

**[1:36:48]** Na-intindihan ninyo? yung Goss-Jordan method,

**[1:36:56]** okay? Kung naintindihan nyo na talaga, gawin nyo nga ito. Sarap. Ang napapansin nyo, nakapag tatlo lang yung unknowns, ginagamit natin x, y, z. Pero pag more than 3 na, ginagamit na natin x1, x2, x3 kasi mauubusan tayo ng letter. Diba? Mauubos yung alphabet. Kaya gumagamit na tayo ng x1, x2, x3, x4. So, of course, gagawin natin ito lahat. Alam nyo, kaya ako gusto ipakita yung limang examples na ito sa inyo. Kasi, kasi po, kasi po ano, ipapakita ng limang ito. yung iba't ibang possibilities na pupwedeng mangyari. Especially yung examples 3, 4, and 5, no?

**[1:37:40]** Pinapakita na ito yung mga iba't ibang pupwedeng mangyari. Ito lang yung mga possibilities na makikita nyo ever. Kaya we will do it one by one, okay? So, specifically, sabi, use the Gauss-Jordan method. So, well, the Gauss-Jordan method tells us to just use matrices, no? Sanbawa, ito, i-convert mo into a matrix, 1, 4, 2, negative 1, guhit, negative 1, 5. That guhit, indicates kung sino yung right-hand side, no? Minsan, to be more particular, minsan naglalagay pa ako na additional line dito, nalagay ko dito yung XY para lang guided ka kung, I mean, inform ka kung ano yung unknowns, anong pangalan ng unknowns.

**[1:38:26]** Naintindihan ninyo? Pero, for now, hindi mo naman kailangan i-identify yung X and Y. Gets? Sige, gawin na nga natin yung Ghost-Jordan method. Okay, may pivot ka na dito. Fine. That's nice. So you wanted to eliminate the 4. So what operation should I do? It's in the second row. pivot on the first, opposite side. Ganun lang. So, first row will not really change. This will become zero as intended. So na. Negative four times two plus negative one. Ay, mali, baligtad ako. Tingnan nyo.

**[1:39:06]** Hindi, tama pala. negative 4 times 2 plus negative 1, so that's negative 8 minus 1, negative 9 ba siya? Ganun ba yun? Can you please correct me if I'm wrong? Next, negative 4 times negative 1 plus 5, puo siyang yan, naghahang ako. or a 9 din. Okay, that's it. Second step, you have a negative 9 as the first non-zero entry, that's bad. So you want it to become 1. So, magmamultiply ako ng negative 1 over 9.

**[1:39:49]** In short, sa second row, magdi-divide ako ng negative 9. Ganun lang yan.

**[1:39:56]** How to become? There you have it. Tama ba? At mapansin nyo, at this point, naka-REF na tayo. na naka-REF na yan eh. They agree? Kaya lang gusto natin RREF para hindi ka na magbaback substitution. Gawin mo na ngayon lahat. So gamit yung pivot na ito, you are now going to eliminate that two by using which operation? So first row yung star. So, sa second row yung pivot, ang multiplier should be the opposite of the star, which is negative 2.

**[1:40:38]** So, again, zero na yung katabi ng pivot natin, so kukopihin mo na lang yun. Diba? Ito magiging zero as intended, tapos, negative 2 yung multiplier times negative 1 plus negative 1. Dito mo na multiply kung nasan yung pivot. Negative 2, change yung sign, negative 2 times negative 1 plus 1 plus negative 1, 1 ba? Ama ba? 1 ba? Negative 2? Utsang, yun, naghahang talaga ako. Pasensya na kayo.

**[1:41:22]** Ang class is or great pentium pagdating sa ganito. 1 ba? Oo no? Nalito kasi ako sa mga sign, particularly, pasensya niya na. At this point, We're going to stop. Naka-RREF na yan, di ba? XY. Di ba? So actually, XY is equal to, I don't know, 1 negative 1. Kung ano yung nasa kanan, yun na siya. Di ba? So anong solution set? ang solution set natin isa-set, unique solution. Ito lang yung solution mo, yung vector na ito.

**[1:42:07]** Okay? Dali lang kapag 2 by 2, no?

**[1:42:14]** Madali nga lang ba? Well, at least hindi siya ganun kalala, no? It's not as bad as we think. Alright, let's move on to the next example. Are you ready? Ito, 3 by 3, medyo malaki na. Can you imagine doing it 10 by 10, ganun? Mga 10 by 15. Charot. Kaya nyo bang gawin yung by hand? Baka isang tanong lang, isang exam na, no? kapag gano'ng kalalaki. Siyempre, hindi ko kayo bibigyan ng gano'n. Grabe naman na hindi naman ako gano'ng kasama. Hindi ko kayo bibigyan ng 12 by 12 na linear system. Pero kaya? I mean, kung tatagain mo, magagawa yun.

**[1:42:59]** Yun nga lang, it will take you a longer time. Kaya yung mga ganon kalalaki, we just ask the computer to do the computation for us. Okay?

**[1:43:14]** Sige, gawin natin ito. So, turn your system into a matrix, 1, 1, 3, 2, 3, A, negative 1, 1, 4, and then here, 357. Again, winawarningan ko kayo, ha? There is an illusion na nakakasunod kayo, akala nyo, marunong na kayo. Kasi nasusundan nyo yung sinusulat ni Sir, ha? Sa totoo lang, gaya ng sabi ko, when you try to practice on your own, dun yung ma-realizes yung sabi ko. Kaya kailangan niyong gawin, you really have to do it actively, kayo talaga, isulat nyo sa kamay para may muscle memory na tinatawag.

**[1:43:59]** Okay? Pivot na yun, star star, so dalawang type 3. First row, yung pivot ay mali, tingnan nyo. Yung star ay nasa second row, yung pivot nasa first, opposite sign. Yung 3 ay nasa third row, yung pivot nasa first row, opposite sign ng 3 is negative 3. Sabayin ko na yung dalawa na paano makasave tayo ng space. Yung pivot row ay hindi gagalawin. Ang magbabago ito, 0. Change the sign, isipin nyo, change the sign of this negative 1, multiply and add. Ganon, negative 1 times 2, negative 2 plus 3, 1.

**[1:44:51]** Negative 1 times negative 1, positive 1 plus 1, that's 2. Negative 1, change the sign in your mind ha? Negative 1 times 3, negative 3 plus 5, I think that's 2. Tama ba si sir?

**[1:45:13]** Did I do it well? Correctly? Did I do it correctly? Sige, thank you. Let's move on to the third row. Syempre, zero na ito. Change mo yung sign, multiply, add. Ito yung pivot row natin, ha? Tandaan nyo kung ano yung may circle. yun yung ating reference, yun yung ating doon natin minumultiply lahat dito. Okay? Para hindi kayo magulo, highlightan ko na lang ng pula para alam nyo saan nagmumultiply. Okay? Negative 3 times 2 plus 8, negative 6 plus 8 is 2.

**[1:45:55]** negative 3 times negative 1 plus 4, 3 plus 4 is 7, negative 3 times 3 is negative 9 plus 17, negative 9 plus 17, hindi ko na kaya yun guys. Ano ba yun? Negative 9 plus 7 is 8. 8 ba siya, hayop?

**[1:46:21]** Okay? Siguro para hindi tayo ma-malito, duplicate ko siya dito, ah, di ba? Ang kagandaan, pag online class eh, kapag sa blackboard to, puwtsang yan, isusulat mo ulit, no?

**[1:46:39]** May mga copy-paste, copy-paste kasi tayo sa online eh. Kapag ano yan, mano-manong chok, imagine nyo yung pagod ko. Alam niyo itong subject na pag tinuturo ko ito dati, tapos face-to-face. Oh my god! Yung buong katawan ko punong-puno ng chalk.

**[1:46:56]** Sige, gilawin natin. Now that we have cleaned the first column, let's now look at this pivot. Pivot na siya except may mga asungot. sa gilid niya na, sa taas at baba niya. So we have to eliminate that. So to eliminate the two above on the first row, E1, 2, negative 2. To eliminate the two on the third row, E3, 2, negative 2.

**[1:47:27]** Okay? Eliminating the two first. Now, dahil 0 na ito, kukopyahin mo na lang yun. 1, di ba ganun yun? Actually, ganito siya o, negative 2 times 0 plus 1, so 1 pa rin, di ba? Ito magiging 0 as intended. negative 2 times 2 plus negative 1, so ganon. Negative 4 plus negative 1 is negative 5. Negative 2 times 2 plus 3, negative 4 plus 3 is negative 1.

**[1:48:14]** Are we good? Tama ba?

**[1:48:19]** Hey! eto, copy lang kasi wala ka namang i-eliminate dyan. Third row, third row, come on, zero na to, copy lang yan, eto zero rin kasi that's intended, magsisimula ka lang dito, okay? Negative two times two plus seven, Negative 4 plus 7, that's 3. Negative 4 plus 8, that's 4.

**[1:48:56]** Naku, nakakaamoy na ako ng mga ano, ng fraction. Nangyayari yun guys ha, there comes a time na may fractions na nalabas. Parts siya ng Puhay. Paano kung naaamo yung fraction? Kasi, this time, mapipilitan na akong gumawa ng pivot sa third row. Agree? And to do that, I have to multiply the third row by one-third para maging one yung three. Kaya lang, by doing so,

**[1:49:33]** Meron na ditong 1, pero dito, 4 thirds. Oh my good lord! Kasama sa buhay yan, na it happens sometimes. At this point, actually naka-REF ka na, kaya lang, you wanted to have an RREF, so tulad kanina, gamit yung pivot na to. Papatayin natin yung dalawang yun nasa taas. So copyin ko ulit ito so you can,

**[1:50:04]** okay?

**[1:50:09]** So eliminate the negative 5 on the first row, the 5 was on the third, change its sign. Diba? So, eliminate the 2 in the second row, the 5th on the third, change its sign. Negative 2.

**[1:50:29]** Okay? You have to master the notations that I am teaching you. Kasi sa next lesson, may pakinabang yan. Manawala kayo sakin. May gamit yung mga notations na yan. Next. sa susunod na lesson. One, ay, sorry. One, zero, zero. Kinopia ko na lang ito, no? Kasi nga, zero, zero yun eh. Wala ka nang gagawin doon, kasi ito mas is zero na. Ang actual work ay nagigay ito talaga. Okay? Paano yung actual work? Change the sign. times four-thirds plus negative one. Ayun na, yung sinasabi ko eh. Scratch ka dito sa gilid.

**[1:51:15]** Negative five times, ay hindi, change the sign pala. Five times four-thirds plus negative one. Oh my good lord! Parang, ay! Nawala yung aking screen! Yan naman!

**[1:51:33]** Sorry. Taglit.

**[1:51:47]** Is it back?

**[1:51:53]** Okay, thank you. So I'm working on this multiplication, 5 times 4 thirds minus 1. Ay, 5 times 4 thirds minus 1. So 20 over 3 minus 1. Ano ba to? 20 minus 3 over 3. 17 thirds. Grabe, no? 17 thirds na walang kadangal-dangal. Okay, next. Ito mula dito hanggang dito hindi mo nagagalawin kasi zero na yun.

**[1:52:33]** Itong 2, mag-zero yan kasi yun yung intention. So, yung change to sign, negative 2, mumultiply mo doon sa 4 thirds, i-add ngayon sa 2. So, this is negative 8 thirds plus 2, negative 8 plus 6 over 3.

**[1:52:56]** Ano sagot? Tama ba si sir?

**[1:53:04]** Tama? Mm-mm. And I think right now we are done. Diba? Anong solution set natin, unique solution ulit, no? Nga lang yung mga vectors mo may ano to, mga floats ito, no? Mga decimals. Yan. So, you got a unique solution to the linear system. Ang tanong ko pala, paano nyo malalaman if your solution is correct? You can check, na? Ilalagay nyo dito yung value ng X, yung Y at Z. So, check nyo lang na lahat ito'y nasasatisfied.

**[1:53:45]** Gusto nyo gawin? Mag-isa kayo. Huwag niyo akong utusan, kasi, ito nyo naman yung mga numbers na yan, 17 over 3. Hayop na yan, no? Kayo na lang mag-check ha. Pakitry ninyo kung nag-work siya correctly. Huwag niyo na ako idama eh. Please. Okay. Are all clear here? Ay, kung nagugutom na kayo ha, kasi it's already 12.30. Kung wala kayo ng pagkain, hayaan nyo lang ako, okay? Anyway, nakasulat naman o, nakasulat naman yung mga stats na... kinagawa ko. Ako naman nagugutom, kaya lang, ako yung hindi pa pwedeng kumain, teacher nyo ako eh. Kaya, kayo, okay lang, sige, kain kayo, puha kayo ng pagkain niya, kasi it's time for lunch, no? Lalo na yung mga may oras ang kain.

**[1:54:43]** Ako kasi para kong ano eh, para kong aso, pusa, kumakain lang ko pag-gutos. Hindi ko talaga yun ang orasan yung sarili kong kain. Okay. Are we good in this example? Can we move on to the next? Sige. Ito na yung ala, next example. 3x3 ulit, pero makikita nyo this time iba yung mangyayari. Let's see kung anong mangyayari. So let's turn this into a matrix first.

**[1:55:25]** Okay? Buti na lang lagi may pivot dito. Kasi kung wala gagawan mo pa ng paraan yan. So to eliminate,

**[1:55:37]** e21, negative 2, to eliminate the 2, to eliminate the 3, e31, negative 3. The first row will not change really, diba? This will become zero as intended, negative 2 times negative 2 plus negative 3. 4 plus negative 3 is positive 1. Negative 2 times 4, negative 8 plus 5, negative 3. Negative 4 plus 3, negative 1. Am I doing correct so far?

**[1:56:26]** negative 3 times negative 2 plus negative 4, that's positive 6 minus 4, that's 2. Ito pala 0 na yun,

**[1:56:41]** okay? Okay, positive 6 plus negative 4, tama, positive 2. Tapos, pa ganon, negative 12 plus 6, negative 6,

**[1:56:57]** negative 6 plus 7, always change the sign of the star, no?

**[1:57:05]** Negative 6 plus 7, 1, 1 ba siya? Sige, 1 siya. Sige. Alright, so let me copy this.

**[1:57:20]** There you go. So, gamit yung pivot na ito, I shall eliminate these two. To eliminate the negative two, I shall use E12, positive two, kasi nasa first row siya, and pivot na sa second. To eliminate the two, E32, change the sign. negative 2. Okay? Yung nasa first column, hindi na yun magbabago. Tapos mag-zero to. Okay? That's the intention. Positive 2 times negative 3 plus 4, negative 6 plus 4, negative 2.

**[1:58:06]** Positive 2 times negative 1, negative 2 plus 2. Zero ba ito? Tama ba? Nasak sa ulo! Ano ba't ang tinasok ko?

**[1:58:21]** Tama ba? Okay, tama. Ito hindi naman magbabago.

**[1:58:29]** Babalik ko na lang yung sweldo ko. Ayun na lang. Ayoko na. Parang torture, you know? Oo, parang kung tin-torture pag gumagawa ng ganito. Sa totoo lang. I don't really like doing this stuff. Ay, nako. Sige, zero. Negative two times negative three positive six. plus negative 6, zero, oh! Negative 2 times negative 1, that's positive 2, plus 1, that's A3.

**[1:59:13]** You know, at this monument, at this moment, I already stopped. Meron akong conclusion. You know why? Sige nga, can you give me- Can you give a conclusion based on what has happened so far?

**[1:59:39]** Yeah, because 0 is not 3, student. So, student, if 0 is 3 in this linear system, what does that say about the linear system?

**[2:00:00]** not true or no solution or inconsistent na yung pang sosyal na terminology, inconsistent na yung ano yan. Correct. Naintindihan niya, actually the highlighted portion is actually equivalent to the degenerate case. 0x plus 0y plus 0z equals 3. Anong sabi ko sa inyo kapag yung right-hand side ay, yung b ay hindi 0, it's puro zeros yung coefficients? This is false always. So, pag may barkada kang napaka-strict ng parents, hindi siya ka pwedeng mag-swimming, pero ang condition dapat sabay magkakasama kayong lahat, ibig sabihin, hindi matutuloy yung swimming. Ang swimming ay na-drawing na naman.

**[2:00:49]** Naintindihan ninyo? So, anong solution set? How do you write the solution set? Hmm?

**[2:01:03]** How do you write, how does one write the solution set?

**[2:01:13]** Walang solution na yun. So how does one write the solution set?

**[2:01:21]** Hindi nyo alam. Pag walang solution, how do you write the solution set?

**[2:01:29]** Ang ginagamit natin sa MATH ay yung empty set. Alam ko sa inyo yung ganito parang zero siya, diba? At sa MATH yung symbol na ito, it's the empty set. Pwede rin ganito, set na walang laman.

**[2:01:47]** The linear system is inconsistent.

**[2:02:01]** Did you understand how does one spot if a linear system is inconsistent, pag may lumabas na all zero sa kaliwa pero yung kanan hindi, that's the time you know that something is inconsistent. Okay? Alright, so pag tinanong kayo, solution set, empty set or null set ang imibigay niya, sabi nga ni student. That's correct. [Redacted: joke about a student's name.] Charot. Choke lang.

**[2:02:38]** Let's try this one. This one is a little bit larger in terms of the number of unknowns, pero hindi naman talaga large kasi tatlong equations pa rin naman ito na, so let's try, sige,

**[2:02:57]** 1, 2, 1, 2, 5, 4, negative 3, 8, negative 8, negative 7, negative 2, negative 1, 5, 4, 6, 2, haba, no?

**[2:03:17]** Can I write this here? Kasya pa ba ng isang step? Sige na nga, kasya pa yan. Oh, wait.

**[2:03:32]** Okay. Buti na lang may libring pivot talagi, no?

**[2:03:39]** Hmm. Okay. How does one eliminate the 2 and the 1? The 2, E2, 1, negative 2. The 1, E3, 1, negative 1. Hmm. Okay. 1, 2, negative 3. It will not change at all.

**[2:04:02]** Okay? This will become 0. Okay? Ito na. Negative 2 times 2 plus 5, 1. Medyo bibilisan ko na ha? Negative 2 times negative 3 plus negative 8, negative 2. Negative 2 times negative 2 plus 1, 4 minus 1 is 3. Negative 2 times 4 plus 6, negative 2. Negative 2 times 1 plus 4, 2. Okay? Next, 0 ito. negative 1 times 2 plus 4, ang kailang ibig sabihin na ito pag negative 1 yung multiplier, ang shortcut na ito sinusubtract mo. Kasi to eliminate this one you have to subtract, tama ba? 1 minus 1, nakuha niya, kaya isusubtract nyo lang, yun yung shortcut.

**[2:05:03]** That's 2. 4 minus 2 is 2. Negative 7 minus negative 3 is negative 4 bang pweste ka? Kanina pa ako, Diyos ko dahil yung utak ko. Hindi matahimik. Subtract natin ha. 5 minus negative 2, this is 7. Let's check. Tama ba yun? Student, mahalaga yung example na ito makinig kayo ha? Mahalaga yung example na ito kasi this is a different scenario. Then, this will become negative 2, subtract at 7. Paano ko na lamang subtraction kasi negative 1 yung ano?

**[2:05:48]** Pag negative 1 yung scalar sa loob, sinusubtract mo lang talaga yun. Okay? Another, another hint. Another tip. Did I do it so far correctly?

**[2:06:06]** Sige, tuloyin natin.

**[2:06:12]** I-MN natin to. Charot. Hindi ko alam yung term. I-eliminate na natin yung 2 tsaka 2 sa ilalim at sa ibaba. Hindi ko na i-re-write para may we have enough space.

**[2:06:27]** E1, 2, negative 2. E3, 2, negative 2.

**[2:06:36]** Here you go. Ah, okay. So, eliminate the 2, well, kukopihin mo na lang ito, kasi ito 0 na siya as intended. Ito ngayon, negative 2, change na sign ha? Negative 2 times negative 2 plus negative 3, that's 1. Negative 2 times 3 plus negative 2, so that's negative 6. plus negative 2, negative 8 ba siya?

**[2:07:04]** Negative 2 times negative 2, positive 4 plus 4, 8 ba siya? No. Next, negative 2 times 2 plus 1, negative 4 plus 1, negative 3.

**[2:07:22]** Check natin isa-isa ulit.

**[2:07:26]** Kaya ko chinecheck. Kasi pag nagkamali ka ng isa dyan, muli na yung mga susunod. Pagpasensya nyo na, medyo mabagal ako sa ganito ha?

**[2:07:39]** Pag ganito kasi parang sabay-sabay tayong nag-aaral. Yung mga ganitong portion ng linear algebra, parang sabay-sabay tayong nag-aaral. Third row! Zero, zero. That's the intention, okay? Negative two times negative two plus negative four, zero siya, diba? Negative two times three plus seven, negative six plus seven, this becomes one.

**[2:08:18]** Negative two times negative two, positive 4 minus 2, it's positive 2,

**[2:08:27]** okay? Next, negative 2 times 2 plus 7,

**[2:08:36]** negative 4 plus 7 is 3. 3 ba siya? Can you confirm please? Okay, so I think some people are computing along with me, so maganda yan and thank you for doing that kasi it makes my work a lot easier. Thank you. Nakita nyo yung susunod na pivot, so may pivot ka na sa first, sa second, sa third, may pivot ka na rin. Kaya lang, may mga asungot pa sa taas, so we will be doing elimination still. Shit! Huh? Kailan ba ito matatapos?

**[2:09:24]** E13, positive A. A23, negative 3. Okay? Ang maganda naman, habang tumatagal, kasi katulad na ito, puro 0 na ito, itong dalawa, kakopyahin mo na lang na, I mean, hindi na maraming-marami talaga yung gagawin mo. Katulad yan, 0 na yung negative 8, kasi may star siya eh. Diba? Next thing to do, negative 8 change the sign, 8, 8 times 2, 16 plus 8, grabe, may umabot na ang 24, galit na galit. Tama ba yun? Hindi ko alam kung tama ito. Bahala na si Lord.

**[2:10:09]** Pag-pray na lang natin matama ito. Ano ito? 8 times 3, 24 minus 3, 21, ayok. I'm not so sure kung tama ito, but we will see. Ito, kopihin natin. 0, 1, negative 2, 3... Ay! Hindi natin kukopihin to! May eliminate pala, no? So, well, kukupihin pala kasi puro zeros na yung ilalim. Tapos ito, zero lang yun. Yung bago, negative 3 times 2, negative 6 plus negative 2, negative 8.

**[2:10:52]** Negative 3 times 3, negative 9 plus 2, negative 7. And finally, I think we are done. I think we are done guys. Is that correct? Oo. Pero kala nyo tapos ng pagdurusa natin. Hindi pa. Kasi ito yung case where the solution is not easily, we will see. Diba, when this turns into a linear system in human form, so in human form, ito pong ibig sabihin yan, x1 plus x2, ah, x3 plus 24x5 equals 21.

**[2:11:45]** x2 minus 2x3 minus 8x5 equals negative 7. And x4 plus 2x5 is equal to 3. So, sir, ano pong solution? Pag-ganyan. hindi mo naman matukoy kung anong value ng x5, kasi ang iniisip nyo palagi, isa lang lagi ang solution, kaya kayo na lilito, no? Sa case na ito, ito yung case where there are infinitely many solutions. So let me tell you why. Kasi tignan nyo ito.

**[2:12:28]** Subukan nyong maglagay ng number na kahit na ano sa x sub 5, tsaka sa x sub 3. Di ba pag naglagay ako let's say 1, lagay ako ng negative 1. Pakita nyo consequently, kakaroon ka na ng value sa x sub 1, x sub 2, at tsaka x sub 4. Maglagay ka ng 5, dito maglagay ka ng 2. Makikita nyo, magkakaroon ka ng another set of values sa x sub 1, x sub 2, at x sub 4. Ang reason behind this is, ang tawag nyo sa mga variables na ito, yung mga nasa unahan, di ba yung mga nasa unahan? We call them the leading variables.

**[2:13:14]** Leading, kasi nasa unahan.

**[2:13:19]** x sub 1, x sub 2, tsaka x sub 4. Ang tawag naman natin sa mga variables na x sub 3 at tsaka x sub 5, kasi parang ang mangyayari, you are free X sub 3 and X sub 5 are free to assume anything, diba? Pwede pwedeng kahit na anong value sa kanila. Ang tawag naman sa kanila mga free variables. Free as in malaya, ha? Hindi free as in libre, kahit alam ko mukha kayong mga libre. Diba? yung free dyan, nag-sabihin malaya kasi you can literally put any values to these variables and then it will give you a solution.

**[2:14:01]** In fact, if you try to solve for the leading variables, mare-reduce mo yung linear system in this manner, x sub 1, is 21 minus x sub 3 minus 24x sub 5. Anong ginawa ko? Ina-isolate kayo x sub 1 sa first equation. If you isolate x sub 2 in the second equation, it becomes negative 7 plus 2x3 plus 8x5, okay? And if you isolate x sub 4 in the last equation, it becomes 3 minus 2x4. Which means, guys, that if I write the vector solution, limang anunce, di ba?

**[2:14:48]** So a vector solution would look like this. You can write it as follows. It becomes 21 minus x3 minus 24x5. x sub 2 is negative 7 plus 2x3 plus 8x5. x sub 3 is x sub 3. I mean, it's free, no? You can assign any value to it. x sub 4 is 3 minus 2x4, while x sub 5 is also 3, so it's just x sub 5.

**[2:15:25]** Nakuha niya? Are you following so far? So ganito. How do you write this more effectively? Ihiwalay niya yung mga scalars lang. dito ano yung mga scalars lang, yan, diba? Negative, ah, 21, negative 7, dito walang scalar sa x sub 3, dito 3, dito wala. Tapos, pag samasamahin nyo yung mga x sub 3, yung mga katabi ng x sub 3, negative 1, 2, 1, 0, 0, at yung mga katabi ng x sub 5, ano sila?

**[2:16:06]** Hmm, negative 24, 8, 0, 0, and then positive 1. Tama ba si sir? Tama ba? Ang idea is that yung x sub 3 at saka x sub 5 are free to assume anything. Ibig sabihin, pag maglalagay kayo ng values sa x sub 3 at saka x sub 5 na kahit na ano, meron kang isang solution. E ilan bang possible values ng x sub 3 at x sub 5? Infinitely many. Kaya, ilang vector solutions meron ka? Infinitely many rin. Did you understand?

**[2:16:53]** So how many solutions are there? There are infinitely many. solutions. Nakanya?

**[2:17:04]** Sino nagsabi na may infinitely many solutions? Kasi, nagkaroon ka ng tinatawag na free variables. Na question, how do you identify sino ang leading, sino ang free variables? dito po. Titingin nyo yung RREF. Diba ito yung X sub 1, X sub 2, X sub 3, X sub 4, at X sub 5? Kung bibilogan nyo yung mga pivots, at titignan mo kung nasa pang anong column sila, yun yung mga leading variables. The leading variables are x sub 1, x sub 2, and x sub 4. Ang tawag niya naman sa other variables na ito, ito yung mga 3 na kuha niya.

**[2:17:52]** Yung mga columns that have 5 votes in them, mga leading variables yun. Yung mga columns naman na walang pivots in them, mga free variables sila. Once nagkaroon ka ng free variables, matik, there are infinitely many solutions, guys. Maniwala kayo sa akin. So ang tanong, how do you write the solution set? Kasi that's what the problem is asking, di ba? Great. So, let me write the solution set. Ano yung solution set natin? Kung infinitely many? Ganito po. Kunin nyo ito. Ito, ito, itong portion na ito.

**[2:18:36]** Ito, ito. Can you see this? Copy. Tap natin. Okay. I-paste ko dito sa aking solution set, paste. Hindi nyo magagawa yan kapag sa notebook nyo walang paste. Yan! Tapos ito lagin nyo na x sub 3 at saka x sub 5 ay mga real numbers. Ibig sabihin, kahit na anong values ng X sub 3 at X sub 5 ay mag-work as, magbibigay ng solution. Okay? So, alimbawa, sinabi ko sa exam, show that the linear system has infinitely many solutions. O yan, nakita nyo na. Ito na yung proof nyo na may infinitely many solutions kasi may three variables.

**[2:19:19]** Okay? Tapos may follow-up question. Give me at least 3 solutions. O, magbibigay kayo ng 3 actual solutions. Anong gagawin nyo? Magka-assign kayo ng value sa x sub 3 tsaka x sub 5. Halimbawa, if x sub 3, x sub 5 are both 0, yun yung pinakamadali, di ba? Anong values ng solution? Or, yeah, ng mga unknowns? Ayan o, yun yung formula. Pag 0 ito, 0 to, pag ito lang, ang solution na makukuha niya ay 21, negative 7, 0, 3, 0. This is a solution.

**[2:19:58]** May kundihanin niyo? Kung sakali naman, let's say, ang x sub 3 ay 1, sa x sub 5 ay 0. Anong solution naman ang ma-degenerate mo?

**[2:20:12]** Ito naman. So, pag 1 sa x sub 3, imagine mo 1 ito, tapos ito 0. Wala na ito. So, parang i-add mo lang ito. Ang solution na mage-generate mo ay 20, negative 5, 1, 3, 0. Did you understand, guys? Iba-ibang values ng x sub 3 at x sub 5 will give you infinitely many solutions. Now, don't worry, this is, this will not be the last time that you will see linear systems with infinitely many solutions. We will have a lot of them later. So, umpisa, mukhang mahirap, pero makakasanayan nyo siyang isulat ng paulit-ulit, kaya, yeah, you will learn.

**[2:21:00]** we will master this definitely. Student, do you have questions or concerns? Student, do you have questions or concerns?

**[2:21:11]** Hello, sir? Hello, sir. Yes. Yung sa X sub 4 po, yung sa isolation, nakalagay 3 minus, hindi sa previous page. Okay. Yung sa isolation ho. 3 minus 2x sub 4, hindi yung tama. 2x sub 5 po dapat, diba? Oh my God! Oo nga, thank you student! Kita nyo, naduling ako. So paano natin imodify ito? Thank you student. Ito yung sinasabi ni student o. Kasi dito ko siya kinuha, inaisolate kayo x sub 4. I miss, so this how, this could have been x sub 5. So what will change? I think this will change.

**[2:21:56]** Tingnan natin ha kung paano magbabago yung mga pinagagagawa natin. Aha. wala ng x sub, so I think dito magkakaroon ng 2,

**[2:22:15]** dito,

**[2:22:23]** tama na ba?

**[2:22:37]** Tama na guys, pakicheck nyo nga. Ulit, yung mga scalars lang, eto, okay? yung mga may x sub 3, negative 1, 2, 1, 0, 0. Okay, yung mga x sub 5, negative 4, 8, 0, negative 2, negative 2 ito, negative 2,

**[2:23:05]** and then positive 1. Okay, so what changed? Ito ngayon, Open ko.

**[2:23:17]** Let's put it over here.

**[2:23:32]** So, what will happen here? So, wala namang magbabago dito. Nakalusot tayo. At dahil siniro ko naman yung x sub 5 dito, okay pa rin ito.

**[2:23:47]** Tama? Okay, so yun lang, medyo nagbago lang yung solution. Actually, malaking error yun. Ayan, yun yung sinasabi ko, diba? Isang number lang yung magkamali. Thank you, student, ha? Isang number lang yung mamali tayo. Nakita nyo, no? Nagkakamali ng malaki. Kaya minsan ako mapagpatawad naman sa pagte-check. Kung sa palagay ko, based on context, alam naman niya yung ginagawa niya eh. Kaya lang dahil negative sign lang ito, kinapalampas ko na yun. Kasi ang kinecheck ko kapag nagchecheck ako ng exam ay yung ability ninyo to recall the concept. Pero yung computation, kasi I will not expect you to execute the computations perfectly. Ako nga, bobo sa ganyan eh, no?

**[2:24:32]** I mean, tsaka sa totoong buhay, hindi naman kayo talaga magma-manual computing yan, no? Yan ay nirarun lang natin sa computer. Ang I will teach you now, na? Kalimbawa, paano natin gagamitin yung mga computers natin to run? Okay, let's say, para consistent lang, makita ko sa inyo ulit through Python. Sige, yung ano, yung Jupiter natin. Sige, sishare ko lang yung aking desktop ulit.

**[2:25:07]** plan ko lang yung aking terminal,

**[2:25:29]** magpapagay ang bagong file.

**[2:25:43]** Pagin natin dito,

**[2:25:55]** sagko sa Jordan method,

**[2:26:03]** okay? So, ilalagay ko lang on the side para makita natin yung aking linear system. Okay guys? Alright, diba so far, ang library na pinapagamit ko sa inyo to do linear algebra stuff, stuff ay, ah, ano ba yun? NumPy, diba? You have to import numpy as NP, karaniwan ito. Now, although numpy is powerful enough, no? It can only do as much. I mean, it can do matrix multiplication, it can do norms, dot product, etc., yung mga standard na linear algebra. Kaya lang, using nampal, you can also do row operations.

**[2:26:46]** Pwede mong i-program, no? Kasi you can retrieve rows and columns in a matrix, no? Using the NPRA function. Kaya lamang wala siyang native na RREF. So, I mean, hindi, hindi native sa numpy ang RREF. Okay, guys? Naintindihan nyo ba? Hindi native sa numpy yung RREF. So, merong isang library na ginawa na yung RREF para sa inyo, para isang enter na lang. lalabas na yung RREF. Ang kailangan nyo, yung SIMPY. Ano na lang?

**[2:27:35]** Ang ibig sabihin natin, natin etong SIMPY, from SIMPY import natin lahat. lahat ng kanyang mga packages, yung mga functions niya. Iisabihin ng star doon ay ini-import natin lahat ng mga capabilities ng Simpy dito sa laob ng ating Python code. Naintindihan niyo? yung simpy ay kapatid naman ng numpy, ginamit ito parang, ay dinevelop ito parang as an extension of numpy kasi, kaya ito simpy, kasi it can do symbolic operations, ano ba yung mga polynomial operations nyo? nakakaintindi siya ng mga algebraic expressions.

**[2:28:18]** Hindi lang siya basta computing, ano, nagkakaroon siya ng algebraic context sa mga pinaggagawa niya. But anyway, gagamitin natin siya as follows. So ayan na, nakaload na yung, ah by the way, kung hindi pa rin pala naka-install yung Simpy sa inyong machine, ipipip install nyo lang din yan. Pip install, simpai. But of course for me I will not do this installation anymore kasi it's already in my system but if not you have to pip install and then restart the kernel. Restart nyo lang itong... para mag-load siya correctly. Okay?

**[2:29:00]** Anyway, paano tayo mag-import? Now, ang maganda dito kapag naka-load na yung simpay ninyo, halimbawa, meron lang ngayong function dito na capital matrix, no? Kumbaga, pag mag-i-input ka ngayon yung matrix, hindi na through npr. Kasi ang maganda dito, pag maka-matrix, sige, kawa tayo ng matrix. Ang first row natin ay 1, 2, 3, ah, negative 3, negative 2, 4. Ano yung right-hand side natin? Ang right-hand side ay 1. Okay, second row, 2, 5, negative 8, negative 1, 6, and 4, okay? At yung last row ay 1, 4, negative 7, 5, 2, 8. Teka na, wala yung last na bracket.

**[2:30:03]** So, yan. Pag in-enter ko yan, binabasa niya na ngayon si A as a matrix. Ang maganda dito, tingnan ko, pag-printin ko si A, well, ganun lang din siya. I mean... yun kasi sya, it's a matrix. It's interpreted as a matrix, guys. Now, paano sya in a RREF? Ang command lang is that, sige, print natin yung RREF na A, lalagay nyo lang dot RREF, yan na lang, tapos, parentheses for the options, but, wala na makilalagay na option, so ganyan lang. A dot RREF, tapos pair of parentheses. Pag pre-link ko ito, ito yung RREF.

**[2:30:45]** Do we have the same RREF? Check na natin.

**[2:30:52]** Ito yung RREF natin, do we have the same? Ito.

**[2:30:58]** Okay. Now. Anong ibig sabihin itong additional na m na to? Ito, ito, ito. May additional na output sya, diba? Parang array or tuple na ang nakalagay 013. Alam nyo yung ibig sabihin ng 013 dyan? Yung 013, yan yung index. Kasi pag malaki na itong matrix na to, mahirap na siyang bilangin, diba? Ang isabi ng 013, yan yung index ng mga columns kung saan nyo makikita yung 5 volts. Column 0, ito yan yung column 0, column 1, tsaka column 3, naroon yung mga 5 volts. Pag malaki na kasi yung matrix na to, medyo mahirap, nakakaduling titigan. pang ilang column ba yung pivot?

**[2:31:41]** So, in short, yung first unknown, yung second unknown, tsaka yung fourth unknown, they are the leading variables. Inibigay niya sa inyo to as an option. Kaya kung gusto nyo i-print, pero kung gusto nyo i-print lang yung RREF lang mismo ni A, Diba ganyan? Dahil yung output niya ay isang tuple, kailangan nyo lang sabihin bracket zero. Dito sa general na output niya, iproproduce niya lang yung unang output which is basically the RREF. Nakuha nyo. So, if I run, makikita nyo, ang nandito lang yung RREF.

**[2:32:26]** Ayun, tindihanin niya. O diba? Sa ganitong form, mahirap makita kung sino ang free variable, kaya ako piniprint ko lang yung RREF ng general para makita ko rin kung pang ilang column yung free, sino yung... What they call this? Leading, tsaka free. Did you understand? The SIMPY function? You can also achieve the RREF using the numpy, kaya lang ikaw ang mag-code. Ito readily available na. Anong mas gusto nyo? Syempre, gusto natin yung readily available na. Diba? Anyway, I'm going to go back. Mayroon ako ipapakita pa sa inyong isa.

**[2:33:16]** Sarang tayo sa iPad ko lang. Surprising enough, maaalala nyo yung calculator na pinakita ko sa inyo last time. Ito, ito. Diba? Do you remember this? calculator. You can download this, or you can download a version of this, or an equivalent app for this, meron na ito sigurado. Ang maganda dito, under the matrix functions, dito yung tingnan yung button na 4, may matrix, di ba? So shift 4. Pag tingnan kayong shift 4, meron ditong row reduce. yung function number 7 returns the reduced row echelon form.

**[2:33:59]** Kagamitin ko siya, just to illustrate. So paano ko ngayon mag-i-input ng matrix? So you have to do alpha 4 kasi nandun yung ano, pipili ka kung anong size. Ang limitation nga lang ng calculator na to, hanggang 7 by 7, hindi katulad ng Python kahit gaano kalaki yan. Naintindihan niya? Kung maliit lang naman, let's say for study purposes, pwede na tong calculator na to. Naintindihan niya? Pero kapag actual data in real life ito, you will be using Python na kasi malaki na. Hindi na kaya ito ng mga calculator na ganito kasimple. Katulad na ito, 3 by 6 itong linear.

**[2:34:43]** Ang linear system ko 3 by 5 pero dahil sa additional na column, yung column of constant sa kanan, you have to add one more. Okay? So lalagay ko dito yung mga constants, 1, 2, negative 3, negative 2, 4, 1, 2, 5, negative 8, negative 1, 6, 4, last row 1, 4, negative 7, 5, 2, 6. There you go. Nakita nyo, instantly lalabas yung RREF.

**[2:35:28]** It took us how many minutes, di ba, to do the RREF, but then... The calculator gives the answer very fast.

**[2:35:41]** Na itunyan ninyo? Basically, the algorithms, the calculators, and Python use usually is based on the Gauss-Jordan but a modified one to avoid division by zeros. May ganun, papaliwanag ko sa inyo. Basically, gumagamit siya ng LU decomposition but for now, wag nyo munang abalahin yung sarili ninyo itong callback. Lahat naman yun ay based lang sa Gauss-Jordan.

**[2:36:09]** Okay? Gets ba? Ang paano gumagamit ng technology to solve linear systems? Patutuloy natin, ha? Itong panglima, I will be leaving this to you as an assignment para meron kayong gagawin. Then we will check it next week, okay? Kung nagagawa ninyo, pwedeng gawin nyo ito ng manual, gawin nyo rin ng using a software and compare your answer, and then we will do it next time. Para meron kayong space to, ah, ito hindi pantay, ito naman ay 4 by 3. So, 4 unknowns, 3 con, ah, 3, ah, 4 equations, 3 unknowns.

**[2:36:53]** Ang tawag natin pala guys sa, pag, ang m ay equal sa n, di ba? Square.

**[2:37:03]** Kapag ang m ay less than n, ibig sabihin yung number of equations is fewer than the unknowns, equations fewer than the unknowns, this is the underdetermined, underdetermined case. Kapag ang m naman ay greater than n, parang itong nakikita nyo, we call it the overdetermined case. Kasi, ang dami mong condition, tatlo lang naman yung hinahanap mo, pero apat yung condition mo. So you get the terminology, pag underdetermined, masyadong kaunti yung condition to uniquely identify the unknowns, limay ang unknowns, pero tatlo lang yung conditions mo.

**[2:37:47]** Napakaswerte mo naman. Under, determine. Naintindihan? Pag over, ang dami mong sinasabi, ito lang naman ang hinahanap. Okay? Okay, so I will now show you one of the ways we use linear systems in real life. Paano ba ginagamit ang linear systems in real life as data scientists? One of its applications, basic applications lang ito, ay yung Tinatag nating polynomial interpolation. Kasi, minsan, ganito. In polynomial interpolation is, you are trying to create a model based on your sampled points.

**[2:38:33]** Imaginin ninyo, may dalawa kang variables na nire-relate, let's say, si variable x at si variable y. Pero dahil imposibleng malaman lahat ng mga attributes ni x at saka ni y kasi, simbawa, si x kunwari ay edad ng tao, si y naman ay yung IQ nila. Gusto mong malaman kung may relasyon ba yung edad tsaka yung IQ? Sabihin, ang IQ ba tumataas habang nag-i-edad? Parang hindi naman ah. So you would like to, I mean, somehow relate to variables. So what you do? Because hindi mo naman kayang interviewin ang mga tao, magsa-sample ka lang ng mga points, no? Sampling, ang tawag dito.

**[2:39:19]** So, ito kunwari yung mga sample, ito yung sample mo kunwari. Sabi niya, nag-interview ka ng N na tao, kinawa mo yung X nila, tsaka yung Y nila, isa-isa. Okay, understand? ang requirement lang dito sa polynomial interpolation problem, yung mga excess dapat magkakaiba. Sabihin, pumuha ka ng taong magkakaibang edad kasi nga, di ba? Naintindihan ninyo? Pero not necessarily na magkakaiba ng IQ yun. Ang magkakaiba lang na required yung mga x. The idea is, we wanted to find the relationship between x and y. So what we wanted to do is we wanted to create a model.

**[2:40:06]** A model is usually a function. A polynomial one is the best. Kasi ang polynomials are computer friendly. Mamaya, papaliwan ako bakit computer friendly ang polynomial. Kasi mga polynomial function only uses the basic computer operations. Addition, multiplication, and subtraction. Yun lang ang ginagamit ng polynomial. Kayang-kaya ng computer niyan. Hindi nga siya nagdi-divide eh, when it computes sa polynomial. So we, the problem ask is to find a polynomial function of degree n minus 1, but n minus 1. Kasi tignan nyo, kapag dalawang points lang ang meron ka, linear yung function.

**[2:40:52]** Degree 1, di ba? 2 points, ang degree ay 1. Kapag tatlong points, tulad yan, meron ka ng parabola or degree 2. N is 3. ang degree ay 2. Kapag apat yung points mo, yung polynomial mo naman, degree 3. You understand? Kaya palaging degree n minus 1. Ang ibig sabihin ng equation na ito, yung polynomial mo nasasatisfy or na-fit yung data mo. Did you understand? Bakit mo naman kailangan ng model? Kasi you wanted to make predictions.

**[2:41:33]** You wanted your machine to learn. Para pag may input ka na another value of x, meron siyang ibubuga na bagong value ng y. Ang tawag nyo nga dito sa mga points at mga training data. Ito yung data na pinatasok mo sa computer para matutuhan niya. Ito ang totoo, hindi naman siya talaga nagtututo. Gumagawa ka lang ng interpolation, pepwedeng regression, pepwedeng whatever. And this is just one of the several models a computer may use to learn. Hindi totoong nag-learn ng computer katulad ng machine learning, correct? Eh, yun yung machine learning na tinatawag natin. Ito yung training data mo. Inelect mo yan from real life measurements, right?

**[2:42:18]** I-feed mo yun sa computer, ituturong saan niya kapag x1, y1, kapag x2, y2, kapag xn, yn. Eh, what if magbigay ako ng value x4, ay, x, let's say, something x. Gamit yung sample data mo, At yung model na na-produce mo, yung polynomial function na yan, for example, po computing niya gamit yung polynomial, yung p of x para makuha yung y. Did you understand how computers learn now? Ganun lang siya. Basically, yun lang naman talaga yung yung tinatawag yung machine learning. But this is just one of the several models, no? Ito yung pinakasimple, unfortunately.

**[2:43:04]** Maraming iba pa na mas complicated and mas efficient now. So as an example, halimbawa yan yung training data mo, no? ang gusto ng alaman ng computer, yung function na yun. So that, kapag let's say, nagtanong ka sa computer, kunwari ito yung X, ano yung Y? Ang isasagot niya, eto, wala siya sa dataset mo, pero kaya niyang i-predict yung magiging Y pag nagbigay ka ng another X. Did you understand? why machine learning is really just a math problem, yet another math problem. Diba? And now, I will show you why this is just linear algebra.

**[2:43:49]** So halimbawa, ito yung polynomial of degree n minus 1 na hinahanap natin that will fit the data or the sampled data. Anong ibig sabihin na ito? Ang isabihin niyan, pag sinabsitute mo yung x sub 1, magiging y sub 1, pag sinabsitute mo yung x sub 2, magiging y sub 2, and so on. Pag sinulat mo yun, ayan o, eto yung case kapag si x sub 1 ilagay ko sa x, magiging y sub 1 siya as a result. So ha? Pag sinabsitute ko sa x sub 2, magiging y sub 2. And so on and so forth. Pag sinabsitute ko sa x sub n, magiging y sub n.

**[2:44:32]** Ang hinahanap natin dito guys, ay yung mga coefficients ng polynomials. Ito yung mga nawawala, ito yung kailangan i-develop ng computer. Pag nahanap mo yung mga values ng mga A, that's how you say that the computer learns or the machine learns. Kailangan malaman ng computer yung values ng mga A na yan. Ang tanong, paano nyo malalaman? Tandaan nyo yung mga X na to, mga numbers lang yan, mga numbers lang ito, given number sila. And do you recognize that this is just a linear system? Ang unknowns natin yung mga A?

**[2:45:12]** Paano yung linear system? Ang announce natin yung A0, A1 hanggang AN-1. Ito yung right-hand side mo. Ito yung mga coefficients. Actually, ang mga coefficients natin yung mga x. Kaya pag sinulat mo siya in augmented matrix, ganito ang itsura niya.

**[2:45:33]** Nakukuha nyo.

**[2:45:37]** Nakukuha nyo ba? Can you recognize? Hello? Do you recognize? So, yan yun. Okay. So, paano natin ilalagay in a matrix yung sample data natin o yung training data? Ang gagawin nyo, yung first column will just all be ones, okay? yung second column, yung mga x-values. Yung third column, yung mga squares ng mga x-values. Hanggang yung last column mo, yung mga excess mo naka-raise lang sa n-1. So pataas ng pataas si exponents. Tapos yung nasa right-hand side mo, are simply the y values, guys.

**[2:46:23]** Nakukuha niya? Papibigyan ko kayo na example. Let's say, you are asked to find a polynomial function of degree 3 which interpolates the following data. Kunwara ito yung data relating x and y, okay? dadaan daw ka mo yung polynomial na degree 3 sa negative 1, negative 2, 0, 0, 1, 0, tsaka 2, 4. Anong function yun? So how do you solve this using linear algebra? To do this, you set up this linear system. Linear system lang ito, kayong matakot guys. Gaya ng sabi ko, 4 kasi ang sampled points mo, kaya may 4 na rows ka.

**[2:47:04]** Kakabitan mo lang ng 1 palagi yung first column, yung column na A0, laging 1 yun. Ito yung mga x mo, nabaga ito laging 1, ito yung mga x, ito mga x squared, ito mga x cubed. Kuha? Ito, pag gini-square mo, square, square, square. Ito naman, cube, cube, cube, cube. Nakuha? At yung right-hand side, ito naman yung mga y.

**[2:47:37]** Okay?

**[2:47:41]** Now this is just for a matter of... Because this is just for illustration purposes, I did the RREF for you para hindi nyo na kailangan gawin. Ito yung lumabas na RREF guys. What does that mean? Ang ibig sabihin po niyan, ang A0 mo ay 0, ang A sub 1 mo ay 0, ang a sub 2 ay negative 1, ang a sub 3 ay 1. Kaya pag nilagay mo siya dito sa formula ng polynomial na ito, 0 to 0, negative 1, tsaka 1. Pag sinimplify mo yan, the model is x cubed minus x squared. In fact, you can verify, no?

**[2:48:25]** x cubed minus x squared, does it work here in your data? Oo. In fact, kapag re-off mo yung mga points na ito siya, yung polynomial function mo na x cubed minus x squared is something like this. It really interpolates your data. And now, your machine learns. And this is the knowledge. Yung function na ito, yan yung knowledge na meron yung machine ninyo. So, the next time na mag-i-input ka sa kanya ng, let's say, .5, alam ng machine mo kung anong ibubuga niyang why. Ako ha? Ito, real-life example where it is actually used by scientists like the biologists. Bakit kailangan natin yung mga ganitong klaseng models? Kasi for example, you wanted to relate the height and the weight of trees, let's say as a a species of trees.

**[2:49:25]** Let's say you're studying a species of trees, you wanted to relate, you wanted to predict its weight by looking at its height. Siyempre, alam nyo, hindi naman every time na interesado ko sa isang puno, sa weight na isang puno, Bumpunutin mo siya, bawal yun, di ba? Hindi naman tayo pwedeng magbunut ng puno basta-basta. So, kung gusto mong sukatin kung anong weight niya, hindi mo pwedeng i-approot mo siya, magagalit ang DEMR sa'yo. So, what we do, kung kumari, let's say researchers kayo, hihingi kayo ng permit sa DNR to sample a few trees. For example, you are allowed to sample tatlo lang, tatlong puno.

**[2:50:08]** Sasukatin mo ngayon yung height nila tsaka yung weight in kilograms. So for example, itong puno na to na Kapag ang height niya, 1.5, 35 kg siya. Pag ang height ay 3 meters, 45 kg siya. Pag ang height ay 3.50 kg siya. So ang gagawin natin yun as scientists, we can only create as much, no? Pero pwede lang tayong gumawa ng model. It's not necessarily the reality, but this is the best that we can give. Kasi hindi ba pwedeng puputuan, hindi ba pwedeng i-approve mo yung puno every time na interesado ka sa weight niya. Maybe yung weight nung kaya interested ang mga scientist may paggagamitan ng data na yan. But, syempre, hindi ka pwedeng bumunot na maraming puno, kaya nagsasample lang tayo. Parang halimbawa, gusto mong malaman kung yung niluluto mong sopas ay masarap na or ano na, uubusin mo ba?

**[2:51:07]** Siyempre, hindi. Mukha ka naman tanga, nagluto, inubos para malaman masarap. Anong gagawin mo? Magto-sampling ka lang. Pukuha ka lang ng konti, di ba? But make sure that your sample is representative. Sabi, hinalo mo dapat yung niluluto mo. Do you understand the idea of sampling? nakuha nyo, yung sinasabi ko sa inya, kaya nag-sampling tayo. May mga reasons why we do sampling instead. So, alimbawa, gamit yung data na ito, let's use a polynomial interpolation model to estimate the weight of a tree of the same species if its height is measured 2 meters. Let's say, 2 meters ngayon, height.

**[2:51:54]** Ano tayo gagamit ng polynomial interpolation model? So, kailangan mo yung polynomial function, degree 2, kasi tatlo yung data mo, tatlo yung sample mo. So, i-arrange mo ngayon. So, lalagay mo dito, di ba? 1, 1, 1, yung mga x mo, 1.5, 3.0, 3.8, kasi isquaring mo,

**[2:52:22]** wala na, 3 by 3, 3 by 3 lang. Tapos lalagay mo dito yung mga y, 35, 45, 50. Tandaan niya ito ay a0, a1, A2. I-RREF natin ito, syempre hindi ikaw ang gagawa nyan. Mukha bang kaya mong i-RREF yan? Kaya nyo ba? Kayo na lang, huwag nyo na ako sama. Hindi ko gagawin yan by hand. So ako yung magkakalculator, bahala kayo kung gusto nyong kamayin hanggang mapanis. 3 x 4. 1, 1.5, 1.5 squared, 45. 1, 3, 3 squared, 45. 1, 3.8, 3.8 squared.

**[2:53:16]** 50, puchang yan. Kita nyo yung mga numbers na yan. Kaya nyo bang kamay niyan? O, hindi nyo kaya yan.

**[2:53:28]** Pero gawin natin yung decimal kasi totoong buhay na numbers ito eh, no? We don't want fractions. O, up to two decimal places na lang. Pwedeng 1, kasi alam ninyo, puro 1 decimal places yung nasa data eh na. So maybe we can use just 1. Ito negative 0.2. Kunwari, yan siya na. So your model, therefore, your polynomial function looks like this. 24.2 plus 7.5x minus 0.2 x squared. So, roughly lang ito. Anyway, model naman ito, hindi yan talaga designed to be exact.

**[2:54:14]** Nakuha niya? So, kung gagamitin niyo yung model na ito to interpolate the Weight of the tree if its height is measured 2 meters, anong gagawin nyo? Pukumpitin nyo yung P of 2. So, kukumpitin nyo ito,

**[2:54:32]** syempre hindi mo na naman kayang gawin yan by hand. So, pukuha ka ulit ng calculator. Kaya, make sure ha kapag exam meron kayong Calculator. Saan ko ba yun na meron kayong mga kanya-kanyang scientific calculator? Is that okay? So, assume, meron kayong lahat noon.

**[2:55:03]** So, nakita nyo, no? So, according to the model, a tree of the same species with height 2 meters will have, sika lang, ayun, will have a weight that is around 38.4 kilograms. Tama ba? Reasonable ba? Reasonable ba yung ano, yung binuga ng model natin? Reasonable na? Yes? So ganon, that's how, and this is also how machine learning, sakala nyo lang ang machine learning is a new thing but it's not really.

**[2:55:49]** Ah, ito may tanong. Can we use the model to estimate the weight of a tree of the same species if its height is 4.2 meters? What do you think is the answer? Let's say, due to limited budget or limitation by the DNR, ito lang yung sample data ko, okay? Pwede ko bang gamitin yung aking data to estimate the weight of a tree with height 4.2 meters? Magagamit ko ba yung model ko? Can I use the model in this case? Ha, guys? Actually, the answer is no. Siyempre, hindi nyo alam na kasi hindi pa kayo sanay.

**[2:56:33]** Kaya nga, siya tinawag na interpolation. Inter. Sinabing inter, nasa loob lang dapat nung data mo. Nagsabihin, yung range of values mo kasi is just 1 point from 1.5 to 3.8, no? So, any x that will fall outside this interval, walang pwedeng, hindi pwedeng magbigay ng conclusion yung model natin kasi our model is an interpolation model. Yun yung kanyang weakness. tandaan niya lahat ng model na meron tayo ngayon, may advantage, may disadvantages, may strength, may weaknesses.

**[2:57:18]** Ito ay isa sa mga weaknesses ng mga interpolating or interpolation model. Ang tanong, Anong gagamitin natin model kapag katulad yan, 4.2 lumabas na siya sa range? No? Lumabas na sa range. Anong gagamitin natin? Doon na papasok yung mga tinatawag nating extrapolation. models. Of course, this is a different kind of mathematics, different type of linear algebra, etc. Maybe pag-aaralan natin, eh, pag-aaralan natin in the future, okay? Mag-alala. In case na, katulad yan, wala na siya within your data range, di ba? Hindi napasok yung 4.2 guys, di ba?

**[2:58:01]** hindi na pa pwede yung interpolation model. Pag gagamit mo lang yung interpolation, pag yung x mo nasa loob nung range ng mga x samples mo. Did you understand?

**[2:58:21]** Hello? Naintindahan niyo yung isa sa mga applications? Sayang, di pa natin natapos kasi we're only three slides away. Kailan 130 na eh? Ano lang naman eh? Yung susunod na ano naman? Yung mga conditions lang. Kailan ba nasasolve ang linear system? Kailan siya walang solusyon? Kailan wala? May sagot tayo. Ano lang, mabilis na lang yan and then we will proceed with the next lesson afterwards. Okay? I hope that you've learned something today, something valuable for today. Ano ko na, stop ko na recording.

**[2:59:05]** Ayan. As always, thank you for the participation and makakakain na kayo. Pwede na kayong lumabas ng meeting. Maraming salamat. Meron bang questions that I need to answer? May natutuhan ba kayo for today? Sana naman.

**[2:59:32]** Sige, marami salamat. End ko na yung meeting, ha. Bye-bye. Thank you, sir. Bye-bye, po. Thank you, sir. Thank you, sir. Thank you, po. Thank you, sir. Thank you, po. Thank you, sir. Thank you, po.

