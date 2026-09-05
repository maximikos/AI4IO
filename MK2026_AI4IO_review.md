# Artificial intelligence and input–output analysis: a scoping review and opportunity map

*by Maximilian KOSLOWSKI @NTNU/Norway. A result of prompting with multiple LLMs.*


## Abstract

Machine learning has begun to enter the compilation and analysis of input–output (IO) accounts, unevenly and without stocktaking. Two recent syntheses of artificial intelligence (AI) in industrial ecology do not identify IO as an adopting subfield, and we find no dedicated review of AI for IO.

This scoping review, reported against PRISMA-ScR, maps the resulting opportunity space. We executed 43 recorded searches across seventeen indexes and repositories between 30 August and 4 September 2026, Scopus, Web of Science and OpenAlex among them, screened 478 records at title and abstract, and included 62 studies that apply learning methods to IO, multi-regional input–output (MRIO) or environmentally-extended input–output (EEIO) objects. We separately screened 2,461 conference contributions to the International Input-Output Association across the meetings of 2014 to 2026. Every opportunity in the map has an evidence tag, an integration tier and a citation, or an explicit record that no study was located under this search.

Two divisions organise the findings. Twenty-nine of the 62 studies apply a learned method to an input–output object; the other 33 apply learning to quantities a conventional IO calculation has already produced, most often to attribute the drivers of a computed footprint. And of the 71 entries in the opportunity map, 18 rest on a study reporting an out-of-sample evaluation while 20 rest on a study that reports none. The map distinguishes the two, because a review that recorded only whether something had been tried would overstate what is known by roughly half.

Three substantive findings follow. Demonstrated work on IO objects sits upstream of the algebra, so that learning improves the inputs to an unchanged Leontief computation and the accounting identities bound the resulting error. The strongest estimation results share an architecture in which a classical, accounting-consistent estimator holds the structure while a learned component supplies a bounded correction inside a hard constraint; the four studies now bearing on that architecture are of uneven quality and two evaluate on synthetic data. And IO propagation coincides with the propagation operator of several published graph-network architectures, which makes the space of defensible model-level proposals small and enumerable.

Two commitments of IO data limit what any learned estimator can deliver: the construct chosen when a symmetric table is derived from supply and use tables, and the monetary unit. Neither is a data problem. The binding constraints on the wider programme are institutional: one open benchmark, no ground truth for the tasks that matter, derived-work licence terms that leave a pooled training corpus unsettled, and a validation architecture capable of confirming its own errors. Six claims of absence made in earlier drafts of this review were falsified by later searches, and Appendix G reports what that record implies for the negative claims that remain.

**Keywords:** input–output analysis; machine learning; artificial intelligence; scoping review; supply and use tables; uncertainty

*Main text: 12,737 words, counted on the markdown source from the heading of §1 to the end of §10, including Tables 1 and 2 and excluding the title block, abstract, appendices and reference list. This exceeds the 10,000 words the editor set. §§4 and 9.2 have been reduced to pointers and their material moved to Appendices F.4 and J, and §3 has been reduced to the four commitments with the full treatment in Appendix H.0. Two further reductions are available and we would rather be instructed than choose unilaterally: moving §5.8 to an appendix removes about 400 words, and moving §6.1 and the remainder of §3 removes about 700 more.*


## 1. Introduction

### 1.1 Four limitations, of two kinds

Input–output analysis faces four persistent limitations. Global tables lag reality by three to five years. Environmental extensions are incomplete for most countries and most substances. Sector resolution is coarse relative to the questions now put to it, from corporate value-chain accounting to deforestation due diligence. And uncertainty, although quantified for nearly fifty years, is seldom propagated into published results.

These limitations are of two kinds, and the distinction organises this review. Some are data limitations, addressable in principle by better estimation. Others are commitments of the framework: fixed coefficients, sector homogeneity, the construct chosen when a symmetric input–output table (IOT) is derived from supply and use tables (SUTs), the import-proportionality assumption, the valuation basis, and aggregation bias. An estimator cannot repair a commitment. It can only be told which commitment it is estimating within.

### 1.2 Why a map is needed

Machine learning has been absorbed by adjacent fields over roughly a decade: life-cycle assessment, official statistics, trade econometrics, supply-chain research. Input–output analysis has absorbed it too, but in a form and in venues that the field's own literature has not registered. A bibliometric review of 1,068 publications at the intersection of industrial ecology and AI does not identify IO as an adopting subfield (Gong et al., 2025). A review of 209 full texts on AI in life-cycle assessment contains no occurrence of "input–output", "MRIO", "EEIO" or "Leontief" (Mensikova et al., 2026). Neither omission is careless. The work exists, and most of it is published in environmental-science and cleaner-production journals, not in economics or regional science, so a search framed around either parent discipline misses it.

Dispersal is the recurring theme, in three forms. A third of our included studies are absent from the two major citation databases, sitting instead in preprint servers, institutional repositories and doctoral theses. Some appear in venues no IO researcher reads; the earliest classifier we located that is trained on the cells of national IO tables was presented to a nuclear materials management meeting (Weimar, Daly, & Wood, 2010), and its evidence is discussed in §5.3, where we also record that it reports no accuracy figure. And the community's own meetings register almost none of it. We screened 2,461 catalogued contributions to the twelve IIOA meetings held between 2014 and 2026. Those of 2014 to 2017 carried no AI or machine-learning contribution in 1,057 papers; those of 2018 to 2025 carried two in 1,143, of which one applies a learning method to an IO object; the 2026 meeting carried seven in 261, with a plenary session on the topic.

Over the same 2018 to 2025 window the published literature we screened produced 31 included studies. That comparison should be disaggregated before it is used, because 19 of the 31 are footprint studies with a learned driver-attribution step and would not be recognised as methodological contributions to IO by anyone reading a conference programme. Restricting the comparison to the 12 studies that act on an IO object gives one conference contribution against twelve published ones. The gap is smaller on the stricter reading and still large enough to be the finding, and on either reading the published studies are overwhelmingly by authors with no visible connection to the Association.

### 1.3 Contribution

This review advances five claims.

First, the demonstrated evidence base is larger than the field assumes and differently composed. Sixty-two studies met our criteria: 29 apply learning to an input–output object, and 33 apply it downstream, to results a conventional IO calculation has already produced. The second group is the one that has grown.

Second, the work that touches IO objects sits upstream of the algebra. An estimate that passes through a balancing operator is bounded by the margins and identities that operator enforces; an estimate substituted for part of the model is not.

Third, the successful architecture subordinates the learned component to a classical estimator and applies the accounting identities by construction. Four studies now embed a balancing, projection or calibration step in or around a learned model. They are of uneven quality: two evaluate on synthetic data, one of them on ground truth generated by the identity its architecture encodes, so the proposition is better attested than in earlier drafts without being better evidenced. §6.2 specifies the study that would settle it.

Fourth, IO propagation coincides with the propagation operator of several published graph-network architectures. This is a restatement of a familiar series expansion, not a discovery, and its use is that it makes the relaxations available to a model-level proposal enumerable. Appendix F.3 gives the correspondence, its three points of inexactness, and one concrete consequence for structural path analysis.

Fifth, the constraints that bind are institutional. The field has one open benchmark, no ground truth for the tasks that matter, licence terms that obstruct pooled training corpora, and a validation architecture that can confirm its own errors.


### 1.4 Scope

We cover AI and machine-learning methods applied to IO, MRIO and EEIO objects across source data, table construction, analysis, forward-looking use and validation. We exclude the distinct literature that applies IO analysis to the environmental pressures of AI itself, such as data-centre electricity and semiconductor supply chains; five such records were identified and excluded during screening. Process life-cycle inventory work enters only at the hybridisation seam. Appendix A states the eligibility criteria in full.


## 2. Method

### 2.1 Review type

Following Grant and Booth (2009) and Munn et al. (2018), this is a scoping review with a mapping purpose, reported against the PRISMA extension for scoping reviews (Tricco et al., 2018), which adapts the PRISMA 2020 statement (Page et al., 2021) for reviews whose purpose is mapping, not effect estimation. The question concerns the extent and nature of activity in an emerging area, outcome measures are incommensurable across studies, and meta-analysis would be meaningless. We nonetheless adopt three practices of systematic review, since the map's value depends on the credibility of its tags: an a priori protocol, a documented search, and study-level appraisal.

### 2.2 Search

We crossed a twelve-term IO set with an eight-term AI set; both are listed in Appendix A.2. Forty-three searches were executed and logged with source, verbatim query, UTC timestamp and record count, across Scopus, Web of Science, OpenAlex, the Directory of Open Access Journals, Crossref, Europe PMC, OpenAIRE, RePEc/IDEAS, EconPapers, CORE, BASE, Lens.org, Dimensions, CiteSeerX, Taylor & Francis, ScienceDirect and general web search. Appendix A.3 gives the log, including the sources that refused access and what was attempted.

Three sources produced most of the result. Scopus and Web of Science were searched on 4 September 2026 with the single Boolean expression in Appendix A.6, applied to title, abstract and keyword fields, no date, language or document-type filter, all databases and editions. They returned 261 and 50 records respectively, 33 of them shared. OpenAlex was searched the same day with the same expression and returned 197 records, of which 93 duplicated the two citation databases and 101 were new. Between them the three sources account for 46 of the 62 included studies.

The overlap between the citation databases and the open index is the methodologically interesting number: 48% of OpenAlex's unique records also appear in Scopus or Web of Science, and the half that does not is where six of our ten OpenAlex-derived includes sit. Four of the six are grey literature the citation databases do not index: a doctoral thesis, two preprints, a national-laboratory conference paper. The others are indexed journal articles, one in *Nature Sustainability*, whose input–output content appears only in the methods and so falls outside a title-abstract-keyword query. The second kind is the more troubling, because nothing in the search design signals its absence.

Two properties of the term set will affect anyone replicating this work. The unqualified phrase "input-output" has near-zero precision even in curated indexes: of the 278 unique records Scopus and Web of Science returned, 145 use it in a non-economic sense, covering control theory, hydrology, neuroscience, agronomic energy budgets and computer file systems. And singular and plural forms of "input-output table" return materially different record sets, as do hyphen and en-dash variants, so all must be enumerated.

We separately screened the papers tables and books of abstracts of twelve IIOA meetings from 2014 to 2026 (Appendix E), and the published outputs of eight official-statistics programmes (§5.8).

### 2.3 Screening and selection

Of 670 records identified, 150 were duplicates: 15 within the open-index set, 33 shared between Scopus and Web of Science, 6 between the citation-database round and the open-index round, 3 within the OpenAlex export, and 93 between OpenAlex and the earlier rounds. Of the 520 remaining, 478 were screened at title and abstract and 379 excluded, most commonly because the phrase "input–output" carried a non-economic sense or because AI was named but not applied. Ninety-nine records were assessed in full and 62 included, of which six are recorded as boundary decisions and flagged as such throughout. Forty-two Europe PMC records could not be retrieved despite repeated attempts and are carried as an explicit residual and not assumed empty.

Every count in this paragraph, in Appendix A.4 and in Table 1 is computed from the deposited record-level ledger by script rather than transcribed. Appendix A.4 gives the flow and the exclusion reasons; Appendix I gives the ledger, for all 379 records from the citation-database and open-index searches.

Four of the 37 full-text exclusions illustrate distinct failure modes a reader may otherwise expect to find included. A conference paper generating an IO table from text-mined Japanese trade records contains no learned model, only text extraction and a deterministic algorithm (Ohsato, Akagi, & Deguchi, 2018). A product-level value-chain method describes itself as leveraging ideas from machine learning but implements a proportional allocation rule (Karbevska & Hidalgo, 2025). A working paper titled *Artificial Intelligence and Input-Output Analysis* uses conventional linkage analysis to study the economic effects of AI (Demirors, Coskun, & Ulger, 2026). And a project report on updating a regional matrix inherits "machine learning" from its umbrella programme while updating the matrix by RAS (Lara-Medina, Ruiz-González, & Alejandre-DelÁngel, 2026); keyword inheritance of that kind is invisible at screening, and is why full-text assessment could not be delegated to metadata.


### 2.4 Evidence status and the definition of AI

Four tags are used and never mixed. *Demonstrated in IO* requires published work applying the method to an IO, MRIO or EEIO object. *Adjacent* requires published work in a neighbouring field that transfers with moderate effort. *Untried* records that no application was located. *Deployed without published evaluation* covers vendor and agency material that supports neither of the first two.

The definition of AI governs every tag, so we state it. We count a method as AI when it fits a function or a representation from data, and the functional form is learned, not specified in advance. This excludes classical statistics with a specified form, biproportional updating, mathematical programming, network science and Monte Carlo propagation. Applying the definition reduces the demonstrated base, and we report the reduction as a result. Appendix C records, for every cell of the map, the tag, its rationale and its citation, or the explicit entry that no study was located.

Appendix B appraises each included study on task, IO object, data, sample size, baseline, metrics, split protocol, dispersion, uncertainty, code and data availability, peer review and replication, following Kapoor and Narayanan (2023) on leakage and Kapoor et al. (2024) on reporting standards. Most fields are unreported in most studies, and no included study reports repeated splits with dispersion on an estimated table.

### 2.5 Use of generative AI in preparing this review

Consistent with the position of the Committee on Publication Ethics and with journal policy, we disclose that the evidence synthesis underlying this review was produced with substantial assistance from large language models operating over partitioned domains, and was cross-compared against independently generated syntheses of the same question. Every adopted claim was resolved to a primary source and read by the authors. Appendix G gives the full disclosure and the record of errors detected at each stage of preparation, including a reference that did not exist and survived one round of checking before detection, and three claims of absence that a later search falsified. The same failure modes are the subject of §8.2, and a review of this literature that concealed them would be worth less than one that did not.

### 2.6 How we state absences, and the limitations of the method

Six claims of absence made in earlier drafts of this review were falsified by searches executed later: three by the citation databases and three by an open index. Appendix G records them. That history governs how absences are stated here. Wherever this review reports that something has not been done, the form of words is *no study located under the search of Appendix A*, and it means exactly that. It is not a claim about the world. Appendix G.4 lists the three remaining negative claims we judge most likely to fall next, with our reasons.

EconLit and Google Scholar were not searched, for the reasons given in Appendix A.3. Non-English literature is not covered, which matters more here than in most reviews given the concentration reported in §8.1; two included studies are published in Chinese with English abstracts, one full-text exclusion is in Spanish, and we have no basis for estimating what a Chinese-language search would add. Screening was conducted by a single reviewer, so exclusion reasons are single-classifier judgements. Eighteen of the 62 included studies have at least one appraisal field we could not fill because the publisher blocked retrieval or the work is embargoed; Appendix B marks each such field *not retrievable* rather than leaving it blank, and Appendix B.0 states what an appraisal table with that much missingness can and cannot support.

Two limitations are specific to the composition of the evidence. Our concept criterion admits unsupervised partitioning methods that the studies themselves label as machine learning, principally k-means and hierarchical clustering, while excluding classical matrix factorisation applied for the same descriptive purpose. That line is defensible but not the only defensible one, and a reviewer drawing it differently would move roughly six studies across it. And the open index that recovered a third of the included set also returned much that a curated database would have filtered: duplicate preprint and published pairs, journal front matter, code deposits, and a number of 2026 working papers with no abstract and no discernible method. Metadata completeness is markedly worse there, and 12 of the 29 OpenAlex records we took to full assessment had no abstract at all.

The deposited supplement carries the verbatim query log, the de-duplication rule, the screening script and the script that generates Table 1, Appendix C and every count reported in §2.3 and Appendix A.4. Two independent screeners applying the criteria of Appendix A.1 to the deposited exports should reach the same 62 studies; that is a testable claim and we have made it testable.


## 3. What an input–output table commits to

Four commitments of IO data bound any learned estimator, and each is definitional rather than empirical. Appendix H states them in full, with the axiomatic results, the accounting relations and the reported magnitudes; this section gives only what §5 to §9 depend on.

**Notation.** Bold upper case denotes a matrix and bold lower case a vector. Let **Z** be the matrix of inter-industry flows, **x** the vector of total output, and **A** = **Z** diag(**x**)⁻¹ the matrix of technical coefficients. Let **f** be final demand and **I** the identity matrix. The Leontief inverse is **L** = (**I** − **A**)⁻¹.

*Fixed coefficients.* Given a transactions table, **x** = **Ax** + **f** is definitional. What is assumed is that the coefficients in **A** are invariant to the perturbation being modelled (Leontief, 1936, 1941; Miller & Blair, 2022; ten Raa, 2005). Learning can improve an estimate of **A**; it cannot establish that invariance, and estimation accuracy is no substitute for it.

*The construct.* Symmetric IOTs are derived from supply and use tables by a modelling choice among four constructs, with axiomatic results (Kop Jansen & ten Raa, 1990; Rueda-Cantuche & ten Raa, 2009), empirical tests on establishment data (Rueda-Cantuche & ten Raa, 2013), and a long argument about the negative entries product technology generates (ten Raa & Rueda-Cantuche, 2013; Almon, 2000; de Mesnard, 2011). A study that estimates "an input–output table" without naming the construct, the valuation basis and the treatment of secondary production has not specified its estimand. Negatives also restrict the admissible estimator class, since relative-entropy methods are undefined on negative cells, which is why GRAS exists (Junius & Oosterhaven, 2003) and was generalised as KRAS (Lenzen, Gallego, & Wood, 2009).

*The unit and the valuation basis.* Monetary tables admit one price per sector pair, so physical inference from them assumes that all buyers of a sector's output pay the same price per physical unit. A physical table is therefore not a unit conversion of a monetary one (Weisz & Duchin, 2006; Hubacek & Giljum, 2003; Giljum & Hubacek, 2009), and the treatment of waste and residual flows within physical tables remains contested (Dietzenbacher, 2005; Xu & Zhang, 2009). Mixed-unit accounts are the constructive response (Merciai & Schmidt, 2018; Stadler et al., 2018), and material footprints computed on monetary tables now report progress against Sustainable Development Goals 8 and 12 (Lenzen et al., 2022). Separately, EEIO intensities are computed per unit of basic-price output while corporate expenditure is recorded in purchasers' prices, and applying one to the other inflates the footprint by the margin and tax share; no classification metric can detect it, since such metrics score labels and not valuation (Mach, Ščasný, & Weinzettel, 2022; André, Mach, & Weinzettel, 2024). An estimator trained on monetary tables inherits price heterogeneity as bias that additional data cannot reduce.

*Aggregation.* Aggregation and inversion do not commute, and the residual is aggregation bias, which is not sign-definite (Lenzen, 2011; Bouwmeester & Oosterhaven, 2013; Steen-Olsen, Owen, Hertwich, & Lenzen, 2014; Zhang, Caron, & Winchester, 2019). Every reported error must therefore state the aggregation level and construct at which it was measured.


## 4. A taxonomy of learning methods for input–output researchers

### 4.1 The axis

Organising methods by learning paradigm (supervised, unsupervised, semi-supervised, self-supervised, reinforcement) partitions how a model is trained, which is not the question an IO researcher brings, and it cannot place conformal prediction, differentiable programming, constraint layers or tool-using language agents, none of which involves training in the usual sense. We therefore organise by inferential task, with three descriptors attached to each entry.

The eight tasks are: T1 estimation of unobserved quantities; T2 assignment and matching; T3 structure and representation discovery; T4 density modelling and synthesis; T5 uncertainty quantification and calibration; T6 constrained inference, optimisation and differentiable computation; T7 causal estimation; and T8 interface, orchestration and verification. Appendix F.4 lists the sub-tasks each covers.

The descriptors are the learning paradigm, which carries the data requirement; the inductive bias, meaning the hypothesis class assumed; and the integration tier defined in §6.3. Appendix C attaches all three to every cell of the map.

Task categories are not disjoint. A graph network that reconstructs a firm-level network performs both estimation and structure discovery. We therefore classify by the inferential target of the published claim rather than by the method used, and state this rule in the caption of every table that uses the scheme.

Self-supervised objectives constructed from unlabelled auxiliary data, such as trade records, business registers or firm descriptions, change what the small number of labelled MRIO observations implies about feasibility, and two studies in our sample exploit this (Köse et al., 2026; Hou et al., 2025); Appendix F elaborates.

### 4.2 Methods

Appendix F defines every method named in this review, with primary citations and the data regime each assumes, and states two properties that are load-bearing later: that conformal prediction requires exchangeability, which IO panels violate, and that its guarantee is marginal rather than conditional; and that hard constraints imposed by projection or optimisation layers differ in kind from penalties imposed during training (Raissi, Perdikaris, & Karniadakis, 2019; Karniadakis et al., 2021), holding to numerical precision rather than approximately. Extensions of conformal prediction to settings where exchangeability fails are the appropriate starting point for IO panels (Barber, Candès, Ramdas, & Tibshirani, 2023; Tibshirani, Barber, Candès, & Ramdas, 2019).

### 4.3 What these methods do not supply

All are function approximators fitted to data. None supplies causal identification, which requires assumptions about intervention that no amount of fitting provides (Peters, Janzing, & Schölkopf, 2017); none creates information absent from the data; and none resolves a definitional choice. The example that will be put to IO researchers is weather emulation, where a graph network matches operational numerical prediction at a fraction of the cost (Lam et al., 2023). That result rests on order 10⁶ to 10⁹ globally complete, physically reconciled states of a stationary, non-reflexive system; input–output analysis has a few dozen partly modelled, revision-prone observations of a non-stationary system whose structure responds to the policies under study. The inference does not carry.


## 5. State of the art along the workflow

We partition the workflow into seven stages and add a cross-cutting account of official statistics. For each stage we state established practice, what has been demonstrated with learning, and what is absent under the search of Appendix A.

One distinction runs through this section and through Appendix B. In 29 of the 62 included studies the learned method acts on an input–output object. In the other 33 it acts on quantities a conventional input–output calculation has already produced: a footprint whose drivers are attributed by a tree ensemble, a set of regional results partitioned by a clustering algorithm, a sectoral series extended by a recurrent network. Appendix B.1 appraises the first group in full; Appendix B.2 tabulates the second.

### 5.1 Source data and extension construction

Established practice combines survey returns, administrative data, energy balances and national inventory reports, assembled largely by hand; the dominant cost is reading source documents and assigning codes.

Learning has arrived here first. Ensemble regression over gridded covariates produces territorial emission estimates for thousands of cities and subnational regions, with prediction intervals and per-country uncertainty reported (Yu, Wang, Manya, & Hsu, 2026). Language models extract inventory values from unstructured documents, where the characteristic failure is a wrong boundary or unit. Geospatial foundation models have located roughly 9,300 Brazilian soy facilities against official registers (Trase, 2026), agency material without peer-reviewed evaluation and tagged accordingly.

Method choice at this stage is better evidenced than elsewhere. Across eighteen gap-filling methods and three greenhouse-gas datasets, interpolation reaches about 97% accuracy for missing time steps and tree ensembles 60–70% for missing emitters, with deep and graph models winning only for complex gaps and only when many covariates are available (Cullen, Marinoni, & Cullen, 2024). Two qualifications belong with those percentages, and not in the appendix alone: the definition of the accuracy metric could not be established from the accessible text, and no split protocol is reported. The comparison a gap-filler must eventually face is not another gap-filler but the truncation error that motivated input–output extensions in the first place (Lenzen, 2000; Lenzen & Dey, 2000).

Three studies now estimate an environmental extension where none exists. ExioML releases factor accounts and footprint edge lists derived from EXIOBASE 3.8.2 for 49 regions and 28 years, and defines a supervised task predicting sectoral greenhouse-gas emissions from value added, employment and energy use, with eight benchmarked models, a 64:16:20 split fixed before tuning, ten repeated runs with standard deviations, and openly deposited data and code (Guo, Guan, & Ma, 2024, 2026). It is the only open benchmark here, and because the task it defines is extension estimation it is appraised in Appendix B.1. A doctoral thesis trains multi-output tree ensembles on 34 Annex I inventories and transfers them to build an industry-resolved account for Saudi Arabia, which publishes a territorial inventory but no residence-based account by industry (Alkhayat, 2026). And a preprint predicts spend-normalised monetary emission intensities for Thai cement and concrete from a procurement graph over electronic tax records, reporting a root mean squared error of 0.042 against 0.185 for the static national EEIO factors it replaces, on a blinded test set of ninety observations, with split-conformal calibration giving 95.2% empirical coverage against a 90% nominal target (Pattanavekin & Ekgasit, 2026).

The third belongs to hybrid life-cycle assessment, which is the seam §1.4 places in scope: deterministic process calculation where physical data exist, EEIO-based completion where they do not, with the learned component estimating the monetary intensity a static national table would otherwise supply. The unified treatment of allocation and construct choice connecting the two traditions (Suh, Weidema, Schmidt, & Heijungs, 2010; Majeau-Bettez, Wood, & Strømman, 2014) is the natural frame for extending it, and no located study has done so.

What is missing is provenance and calibration. Model-produced extension cells enter databases without a flag distinguishing them from measured values and without an interval.

### 5.2 Supply-use compilation and the construct choice

Established practice is described in §3. The claim available here is narrower than an absence of activity.

Three studies place a learned component in the compilation path. Large language models perform the firm-to-sector attribution behind a subnational and international coupling MRIO for 2017: retrieval gathers business scope and product descriptions, a fine-tuned open-weight model classifies firms to sectors at a reported accuracy of 0.96, and the micro-records are aggregated into the intermediate matrix and balanced by GRAS (Hou et al., 2025). Import and export deviations against customs statistics are 2.53% and 5.09%, against 17.82% and 16.16% for EXIOBASE. Neither the corpus size nor any train–test partition for the classifier is disclosed, so the 0.96 has no protocol behind it. A random forest estimates the biophysical flood-mitigation capacity that, after hydraulic routing and valuation, populates a SEEA ecosystem accounting supply and use table (United Nations et al., 2014; Wang, Zheng, Chen, Hu, & Ouyang, 2026); we record it as a boundary decision, because two deterministic steps separate the learned quantity from the tabulated one, and because that is not a product-by-industry supply-use table in the sense of §3. Concordance estimation, treated at §5.4, is compilation work by any reasonable reading.

The construct choice itself is untouched under this search. No study predicts which technology and sales-structure assumption best reproduces held-out establishment data, treats secondary production, or estimates the make matrix. The absence has a defensible reason, since the construct choice is axiomatic rather than statistical. The sub-problem Rueda-Cantuche and ten Raa (2013) show to be empirically testable is a supervised problem with a defined label, but §9 states the constraint that follows from how few economies could supply an instance.

### 5.3 Balancing, updating and regionalisation

Established practice is biproportional updating and its descendants, with donor-based disaggregation and non-survey regionalisation. Balancing enforces the accounting identities and is what makes an estimate an account; for strictly positive tables it is also posterior inference, RAS corresponding to uniform relative uncertainty on every cell (Rodrigues, 2014). Projection variants have been compared systematically (Temurshoev, Webb, & Yamano, 2011; Valderas-Jaramillo, Rueda-Cantuche, Olmedo, & Beutel, 2019), and Bayesian updating under a sparsity-inducing prior is available (Tsionas, 2020). KRAS generalises the balancing operator to inconsistent and unreliable constraints by attaching a reliability weight to every datum (Lenzen, Gallego, & Wood, 2009), which makes those weights an estimable object; §9.2 records the proposal to learn them.

The learned literature here begins earlier than the field assumes, and the early record is not encouraging. Papadas and Hutchinson (2002) train a backpropagation network to forecast technology coefficients and multipliers on United Kingdom tables and apply RAS to the same tables for comparison. Many individual forecasts are more accurate from the network; RAS is more accurate overall, by a margin the authors describe as too small to be systematic. The fair summary is a tie in which the conventional method holds its ground, and we use that formulation throughout. Two contemporaneous papers propose neural formulations without benchmarking them (Wang, 2001; Ito, 2000). In 2010 a random forest was trained to discriminate a country attribute from a selected subset of the 2,304 cells of national OECD tables, across 93 country-year tables (Weimar, Daly, & Wood, 2010); it reports no accuracy figure, no baseline and no validation protocol, so whether it worked is unknown. Between 2003 and 2015 we located two studies in total.

Two recent results define the frontier. Zhao, Shuai, Qu and Xu (2022) train a network on the residual between a RAS estimate and the observed table and add the correction back. On United States summary tables this raises the coefficient of determination for one-year-ahead estimation from 0.64 to 0.87 and reduces the median absolute percentage error across cells from 37% to 11%, with the improvement carried through to a national carbon-footprint application. Whether the corrected table is rebalanced after the residual is added is not stated, and it should be: an unbalanced correction is not an account. De Pretis, Tortoli and Caria (2026) place an iterative proportional fitting step inside the generator of a generative adversarial network, so that generated regional tables satisfy their margins by construction, and add residual boosting. Against an improved-RAS benchmark they report 0.94 against 0.85 on the coefficient of determination, and raise the correlation of diagonal own-sector entries from 0.32 to 0.82. The paper does not state where the margins come from at prediction time. If they are given, the estimation problem is smaller than it appears and the constraint binds a partly known object; if they are estimated, the hard constraint binds an estimate rather than an account. The distinction decides how much the result supports §6.2, and one sentence would settle it.

Three appraisal points accompany those figures and are set out in the notes to Appendix B.1, the sharpest being that a network trained on the RAS residual of United States annual tables may in part be learning the compiler's own updating procedure.

Two further studies pursue the same object, and neither reports a usable figure. Fukui (2026) predicts each item of a regional table separately and then balances the predictions, reporting higher accuracy than matrix balancing under the idealised assumption of known row and column sums; per-item figures are not reported, and beating a comparator handed the true margins is a strong claim that should not be repeated without them. It is the same author's sequel to Fukui (2025), so the two are one research line and not independent corroboration. A Russian-language preprint forecasts the direct-cost coefficient matrix with convolutional networks, arguing that published sectoral forecasts can substitute for the intermediate-demand data RAS and cross-entropy require (Potashnikov, 2022); its figures could not be retrieved, and we record the design, not the result.

Non-survey regionalisation already contains the design principle this review advances: a non-survey prior corrected by superior data where available (Round, 1983, 2003; Lahr, 1993), with holistic distinguished from partitive accuracy (Jensen, 1980), which anticipates the impact-weighted loss of §9, and with every method biased in a direction set by the parameters chosen (Bonfiglio & Chelli, 2008). Location-quotient variants (Flegg, Webber, & Elliott, 1995; Flegg & Webber, 2000; Kronenberg, 2009; Flegg & Tohmo, 2013; Flegg, Mastronardi, & Romero, 2016) and cross-hauling corrections (Többen & Kronenberg, 2015) are the incumbents a learned regionaliser must beat. Two studies have made that comparison on Japanese data. Pakizeh and Kashani (2022) report that tree ensembles and neural networks outperform location-quotient formulae; their figures could not be retrieved, so the direction of the result is on the record and its size is not. Fukui (2025) reports that interpolating between observed regions to enlarge a small training sample improves a neural estimator against both location-quotient and RAS baselines, on an 80:20 split with three held-out cities.

A third route bypasses the table. Tranos, Carrascal-Incera and Willis (2023) predict interregional trade flows for United Kingdom regions and fifteen sectors from hyperlinks between archived commercial websites, training random forests on existing trade estimates and forecasting forward in a rolling design with cross-validation inside each training window. Reported coefficients of determination exceed 0.9, and predictions are disaggregated to sectors and local-authority units for which no trade data exist. This is the most appropriate evaluation protocol in our sample; the qualification concerns the target, since the ground truth is itself a modelled estimate, so the exercise shows that web traces reproduce an existing estimation procedure at finer resolution.

### 5.4 Classification, concordance and valuation

Established practice is hand-maintained concordance matrices, manual coding and expert selection of proxy datasets. This is the highest-volume part of the workflow and the part where learning is most widely deployed.

Concordance estimation has been attempted directly. Fazal, Ma, Baynes and Lenzen (2026) apply deep learning to textual sector labels to predict concordance matrices, reporting up to 85% accuracy across a range of matrices, and frame the contribution as labour saving. This is the first learned treatment of an object at the centre of multi-source compilation, and it is published in this journal. One caution belongs with the figure: a concordance matrix is sparse and binary, so an unweighted accuracy admits a high score from a predictor that is right mainly about zeros, and the accessible text states neither a class-balanced measure nor a split protocol. The reporting convention this result establishes will matter more than the number.

Classification of corporate expenditure into EEIO sectors remains the largest application by volume. On the only public benchmark, spanning 295 sector classes, the best method assigns the correct class first for 57.3% of items and places it in its top three for 72.2% (Dumit et al., 2024); the benchmark items are synthetic, generated by a language model to mimic a private vendor dataset, which is the pattern §8.2 identifies as circular validation, and its authors are affiliated with a vendor of the product. Retrieval with hierarchical language-model classification over company descriptions assigns the correct class first for 83.7% of cases while still carrying large errors in the resulting emission estimates (Guo, Qian, Credit, & Ma, 2025). Matching household products to sectors without task-specific training reaches about 48% (Balaji, Guest, Vunnava, & Kramer, 2023), and a conference paper reports the same task on general-ledger transactions against the manual mapping that is current practice (Mudiyansege, Kumari, Pepper, McDowell, & De Zoysa, 2025), with figures not retrievable. None of these five reports a split protocol, and their figures are not comparable, since label spaces, input quality and metrics differ.

Valuation belongs at this stage. As §3 sets out, applying basic-price intensities to purchaser-price expenditure overstates footprints in one direction, and no accuracy metric in the classification literature can detect it. We located no quantification of its aggregate size under the search of Appendix A, which for this claim included a targeted search of vendor and practitioner material as well as the academic sources, recorded in Appendix A.3. We state it as a large and unquantified systematic error, and §9 asks how large.

Trade-data reconciliation now derives conversion weights across classification vintages from observed flows and not from assumption, recovering roughly three million additional annual observations (Bustos et al., 2026). The divergence literature indicates where harmonisation effort should be directed: once satellite accounts are aligned, consumption-based estimates converge substantially, and the emissions vector rather than the economic structure is the dominant remaining source of difference (Moran & Wood, 2014; Owen, Wood, Barrett, & Evans, 2016; Giljum et al., 2019).

### 5.5 Structural analysis and footprinting

Established practice is multipliers, key-sector analysis, structural decomposition, structural path analysis and fields of influence (Hewings, Sonis, & Jensen, 1988; Sonis & Hewings, 1992; Dietzenbacher & Los, 1998; Lenzen, 2003; Temurshoev & Oosterhaven, 2014), on a network whose importance for aggregate fluctuations is established (Acemoglu, Carvalho, Ozdaglar, & Tahbaz-Salehi, 2012), applied through multi-regional models to a widening set of pressures (Wiedmann, 2009; Weinzettel et al., 2013; Wilting et al., 2017; Li, Wiedmann, & Hadjikakou, 2019).

This stage holds the largest number of included studies. Twenty-one of the 33 studies in the downstream group compute a footprint or a set of embodied flows with a conventional MRIO calculation and then apply a learned model to the result: tree ensembles and multilayer perceptrons with Shapley attribution to rank drivers of embodied carbon, minerals, water or energy (Fang et al., 2023; Zhao & He, 2026a, 2026b; Ge, Qu, et al., 2026), and clustering to partition provinces or countries by their computed footprints (Liu, Liang, Xu, & Ye, 2023; Zhi et al., 2023; Liu, Liang, Zhou, et al., 2025; Faridzad, 2025, 2026).

That template is best read as a continuation of an existing tradition rather than as a novelty. Structural decomposition analysis already attributes a change in a computed indicator to changes in its components, and the newer work substitutes a fitted model and a Shapley attribution for an index-number decomposition (Dietzenbacher & Los, 1998). Read that way, the learned step answers the question SDA answers, on cross-sectional rather than temporal variation, and with an attribution that carries no accounting identity behind it. Two properties follow. The learned component never touches the accounts, so nothing in it can improve or damage an estimate of a table. And the reporting is thin: six of the 33 report an alternative predictive model as a baseline, two report a train–test protocol, and none reports repeated runs with dispersion. The best reported is Chen, Zhu, Wiedmann, Yao, Xu and Wang (2019), who classify 25,661 survey households into five energy-requirement bands derived from a provincial MRIO table and report 68.7% accuracy for a single decision tree against 89.4% and 89.5% for random forests and gradient boosting, on an 80:20 split with five-fold cross-validation.

Direct integrations of graph learning with an IO framework are rarer. A spatial-temporal diffusion graph convolution network represents United States annual tables from 1997 to 2024 as weighted graphs over 71 industries and forecasts the Leontief inverse forward, combining the result with fixed USEEIO intensities to obtain construction-sector footprints under scenarios (Kim, Choi, & Hong, 2026). A graph attention model predicts sector outputs from the inter-sectoral structure and reports lower error than four learned baselines (Zheng et al., 2026), none of which is the linear IO calculation it proposes to improve on. A recurrent network supplies time-varying multipliers in a Ghosh supply-side model for China's marine sectors (Jin & Zhang, 2025), and the interpretive cautions attaching to that model remain (Oosterhaven, 1988, 2012, 2022; Dietzenbacher, 1997). A deep deterministic policy-gradient agent chooses interventions on a cascade model built over an IO table and balanced by RAS (Li, Zhang, Hu, & Zuo, 2024), the only reinforcement-learning application we located. And one study uses gradient boosting to supply the nuisance functions of a double machine-learning estimator whose outcome is a value-chain resilience indicator computed from China's interprovincial tables (Huo, Bian, He, & Lv, 2025); it is the only instance we found of a learned method used for causal identification on a quantity the accounts produce, and the identification rests on the research design and not on anything the accounts contribute.

Firm-level network reconstruction remains the more consequential development. Reconstructions validated against Ecuador's complete value-added-tax production network reproduce firm-level systemic risk well enough to identify most of the highest-risk firms from sector-level tables alone (Fessina et al., 2026); supervised link prediction achieves comparable ends where firm data exist (Mungo, Lafond, Astudillo-Estévez, & Farmer, 2023); and language models now reconstruct temporal, multi-relational firm networks at scale from unstructured text (Köse et al., 2026). On Hungarian data, 32 firms of 91,595 account for systemic risk equivalent to roughly a quarter of national output, and network position predicts systemic importance better than size does (Diem, Borsos, Reisch, Kertész, & Thurner, 2022).

### 5.6 Forward-looking analysis and shocks

Established practice spans the dynamic input–output model (Leontief, 1970; Duchin & Szyld, 1985), trade models in which bilateral flows are determined and not assumed (Duchin, 2005), adaptive regional models (Hallegatte, 2008, 2014), non-linear programming for disasters (Oosterhaven & Bouwmeester, 2016; Oosterhaven & Többen, 2017; Koks & Thissen, 2016), and the pandemic-era dynamic models (Pichler, Pangallo, del Rio-Chanona, Lafond, & Farmer, 2022).

The most instructive recent result is a replication. Alleman, Schoors and Baetens (2023) validate a supply- and demand-constrained model on Belgian data against four independent series, reporting a value-weighted mean absolute deviation of 4.69%. Relaxing the strict Leontief production function helps, but the degree of relaxation barely does. What does the work is the input-criticality matrix, an expert survey classifying each input to each sector as critical, important or non-critical, which prevents the model concluding that restaurant closures halt construction.

The most common learned pattern at this stage is weaker. A neural or grey-neural forecaster projects an aggregate or sectoral series forward, and a fixed IO structure allocates the projection across sectors. The earliest instance distributes a combined grey-model forecast using coefficients read off the table (Liu, Moreno, & García, 2016). The design recurs in a research programme coupling IO or MRIO accounting with convolutional and recurrent forecasters for water and carbon (Ma et al., 2023; Zhou et al., 2023; Wang et al., 2024; Li, Li, Huang, Wang, Liu, et al., 2026; Li, Li, Huang, Wang, & Li, 2026), and in work that reconstructs missing MRIO years biproportionally before forecasting the resulting footprints (Zou, Li, & Han, 2025, 2026). In this design the accounting identities constrain nothing about the learning problem, the forecast inherits whatever the fixed coefficients assume, and the step that touches the table is conventional. One coding caution: in this literature "GNN" sometimes denotes a grey neural network rather than a graph neural network.

Emulation is the second thread: 11,076 runs of a spatial agent-based model support one million emulated policy runs across 46 regions (Furtado & Andreão, 2022). Near-real-time MRIO compilation from extrapolation and optimisation, with no learning, is the incumbent any learned nowcaster must beat (Huo, Chen, Hubacek, Zheng, Meng, & Guan, 2022). One conference result sets the expectation for cross-country transfer: a random forest predicting a 9 × 9 inter-industry matrix achieves 36% average relative accuracy on held-out countries, with verification errors for Vietnam from −38.4% to +216.1% (He, Mi, & Guan, 2025).

### 5.7 Validation, computation and communication

Established practice is balance checks, cross-database comparison and expert review, professionalised by open toolboxes (Stadler, 2021; Pauliuk & Heeren, 2020).

This stage is the least developed and, we argue, the most important. We located no published, learned anomaly detection on coefficient matrices under the search of Appendix A; compilers perform outlier detection, but not with learned methods and not with published evaluation. Calibrated intervals on model-produced cells now exist for subnational inventories (Yu et al., 2026) and, through split-conformal calibration, for learned monetary emission intensities (Pattanavekin & Ekgasit, 2026), but not for the cells of an input–output table.

The conformal result will be cited as a precedent, so two qualifications belong with it. Coverage of 95.2% is measured on ninety held-out points, and a binomial interval around it spans roughly 88% to 99%, so it is consistent with correct calibration and with substantial over-coverage alike. And split conformal requires exchangeability between calibration and test sets, the assumption §4.2 identifies as failing on IO panels: the 132 observations sit in seven supplier cliques, so either a clique straddles the split and the two sets share a firm, or cliques are held out whole and the effective sample is seven. The objection applies here too, in a different form.

One study treats the solution of the Leontief system as a learning problem. Benhari, Kaicer and Driss (2026) map interval-valued coefficient matrices and demand vectors to interval solutions of (**I** − **A**)**x** = **f**, against four classical solvers on a six-sector illustration. Coefficients of determination exceed 0.97, and coverage before post-hoc width calibration ranges from 1% to 25% against a 90% target. The claimed advantage is amortised cost over repeated solves, the right claim for a Tier 2 result, demonstrated at a scale where no such advantage exists.

The most consequential absence is benchmarks, and it is now one absence smaller. ExioML supplies an open dataset with a defined task, repeated runs and reported dispersion (Guo, Guan, & Ma, 2026). What still does not exist is a held-out national supply-use table for scoring estimation methods, a labelled classification set built from real ledgers, or a gap-filling benchmark with realistic missingness, even though split choice alone moves reported accuracy substantially on a life-cycle inventory imputation task (Zhao, Jiang, Xu, & Tu, 2025).

### 5.8 Official statistics: the adoption channel

The evidence with the clearest bearing on IO practice comes from statistical offices, because they report production status, not research results.

The Machine Learning Project of the High-Level Group for the Modernisation of Official Statistics has run multi-country pilots in classification and coding, with reported accuracies spanning roughly 70–95% (United Nations Economic Commission for Europe, 2021). The United States Bureau of Labor Statistics assigns codes automatically for more than 85% of cases with 39% fewer errors than manual coding, and the Office for National Statistics reports 81–85% accuracy against 50–53% for the rule-based tool it replaces. Two cautions travel with these figures: only a minority of pilots reached operational status and the project's own summary states that none demonstrated a direct financial benefit, and coverage must not be conflated with accuracy, since the incumbent is more accurate on the subset it matches and far less accurate overall.

Three programmes bear directly on IO compilation. Eurostat's AIML4OS carries work packages on machine-learning editing, imputation, large language models and synthetic data, and one on mapping supply-chain networks from company-level data that is an input–output problem being solved outside the input–output literature. Destatis has published a quality framework for machine learning in official statistics (Dumpert, 2025), and Statistics Canada quality dimensions for statistical algorithms including explainability and uncertainty quantification (Molladavoudi & Yung, 2023).

We located no instance of a statistical office deploying a learned step in the compilation of a published supply-use or input–output table. What the research literature supplies instead is a provenance problem in miniature. Hou et al. (2025) is a compiled, documented, openly deposited MRIO whose sector attribution rests on a language model, and a user of that database who does not read its methods section will not know which figures are model output. That is an academic artefact rather than an official one, and we present it as an illustration of the provenance risk rather than as evidence of official adoption. The adoption channel remains open and, on present evidence, unused for compilation itself, which is the practical case for the provenance flag proposed in §9.3.


## 6. Three propositions

### 6.1 Propagation

The Leontief inverse admits the Neumann expansion

  **L** = (**I** − **A**)⁻¹ = **I** + **A** + **A**² + **A**³ + ⋯,  (1)

which converges when the spectral radius of **A** is below one. Each term propagates demand one step further along the directed, weighted graph whose weighted adjacency matrix is **A**, which is the operation graph networks call message passing (Gilmer, Schoenholz, Riley, Vinyals, & Dahl, 2017).

The correspondence is a translation of a standard reading (Miller & Blair, 2022) and not a discovery, and it is inexact in three respects that Appendix F.3 states precisely. Appendix F.3 also sets out its use: it makes the relaxations available to a model-level proposal enumerable, and it yields one concrete consequence, that truncated message passing is the same computation as truncated structural path analysis, so the extraction heuristics developed for structural paths transfer directly to the choice of propagation depth. Any model-level proposal must relax at least one of four restrictions: R1 linearity, R2 fixed weights, R3 static coefficients, R4 the unit and the node set. R4 is the least explored and, in our view, the most promising, because accounts are rectangular product-by-industry systems and a model that respects that structure estimates something the accounts contain, while one that assumes a square symmetric **A** has adopted a construct without saying which.

### 6.2 Constraint embedding

The strongest estimation results in §5.3 differ in method and share an architecture: a classical, accounting-consistent estimator holds the structure, and the learned component supplies a bounded correction. In one it is a residual added to a RAS estimate; in the other a generator whose output passes through a balancing step.

Four studies now bear on that architecture, and they are of uneven quality. De Pretis et al. (2026) embed iterative proportional fitting in a generator, so that margins hold by construction on real national and world tables, though the paper does not say where those margins come from at prediction time. Fukui (2026) balances predicted cell values after the fact and reports no per-item figures. Zhang et al. (2026) inject the original node features at every message-passing layer, a device motivated by **L** = **I** + **AL**, and isolate its contribution by ablation, raising the root mean squared error from 144 to 172 when it is removed; the evaluation is on synthetic data whose targets were generated by the identity the architecture encodes. Pattanavekin and Ekgasit (2026) calibrate a learned intensity by split conformal prediction, on 42 fitting observations. Two of the four evaluate on real data, one of those does not report the figures, and one of the synthetic evaluations is circular by construction. The proposition is better attested than in earlier drafts of this review without being better evidenced.

We therefore state it as a proposition. Learned components subordinated to an accounting-consistent estimator, with constraints applied by construction and not by penalty, will outperform end-to-end learned alternatives on IO estimation tasks and will degrade towards the classical estimator, and not catastrophically, when the learned component fails.

Four considerations keep it a proposition. The real-data evidence is two studies, both single-country, both benchmarked against RAS variants on tables that are themselves partly RAS-derived, which is the circular validation of §8.2 operating on the evidence for the proposition. Neither has been independently replicated. The one head-to-head comparison of a learned updater against RAS on a common set of real tables that we located ended in a tie (Papadas & Hutchinson, 2002). And no study reports whether its corrected table is rebalanced after correction. §9 specifies the replication that would settle it.

The mechanism is straightforward. Projection layers make stated linear equalities hold to numerical precision, so a violation of the accounting identities becomes impossible rather than merely unlikely. They do not make the table correct: constraints redistribute error without removing it, and a balanced table that is wrong is more dangerous than an unbalanced one, because balance is the profession's principal check.


### 6.3 Three tiers of epistemic risk

Feasibility and impact are insufficient axes, because the proposals with the highest impact are also those most capable of producing confident wrong answers. We stratify by distance from the model and state, for each tier, the evidence sufficient to accept a result.

Tier 1 places learning upstream of the algebra, filling, classifying, imputing or nowcasting the inputs while the computation is unchanged and accounting consistency is preserved by construction. Nearly all demonstrated work sits here, and sufficient evidence is out-of-sample accuracy against a held-out account, with dispersion across splits.

Tier 2 treats learning as computational substrate: differentiable pipelines, randomised linear algebra, sparse solvers, surrogates, with the model unchanged. Epistemic risk is low and leverage high. Sufficient evidence is numerical agreement with the exact computation together with a cost saving.

Tier 3 substitutes learning for part of the model. Sufficient evidence is a demonstrated failure of the linear model on the question at hand, constraints retained, and out-of-sample validation against an independent series. Alleman et al. (2023) meet that standard; few others in this literature do.

The tiers rank the evidence a result requires before it can be believed, and Appendix C attaches a tier to every cell of the map.


## 7. The map

Table 1 gives the map at task level. Appendix C gives the complete version, with a citation or an explicit record of absence for every entry, the rationale for every tag, the integration tier, and the learning paradigm and inductive bias where an entry is demonstrated. Table 1, Appendix C and every count reported from them are generated from one source list by script, so the two cannot disagree.

The tag scheme distinguishes two kinds of demonstration, which earlier drafts of this review did not. ▲ records a study that reports an out-of-sample or held-out evaluation on an IO object. △ records a study that acts on an IO object but reports no such evaluation, whether because it reports no metric, no protocol, or because the full text could not be retrieved. The distinction matters: on the tags below, 18 entries rest on an evaluated result and 20 on an unevaluated one, so a map that recorded only whether something had been tried would overstate what is known by roughly half.

**Table 1.** Opportunity map: inferential task by workflow stage. Symbols: ▲ demonstrated on IO objects with a reported out-of-sample evaluation; △ demonstrated on IO objects without one; ◆ demonstrated in a neighbouring field; ○ no application located under the search of Appendix A; – not a meaningful combination. Bracketed numerals are integration tiers (§6.3). Superscript numerals index the entries described in Appendix C. Entries are classified by the inferential target of the published claim, not by the method used.

| Task ↓ / Stage → | S1 Source data | S2 SUT and construct | S3 Balancing and regionalisation | S4 Classification and valuation | S5 Structure and footprints | S6 Forward-looking | S7 Validation |
|---|---|---|---|---|---|---|---|
| **T1** Estimation | ▲[1]¹ △[1]² ▲[1]³ △[1]⁴ ▲[1]⁵ | △[1]⁶ ○[1]⁷ | ▲[1]⁸ ▲[1]⁹ △[1]¹⁰ △[1]¹¹ △[1]¹² | ◆[1]¹³ | △[1]¹⁴ | △[1]¹⁵ △[3]¹⁶ | ○[1]¹⁷ |
| **T2** Assignment | ◆[1]¹⁸ | △[1]¹⁹ ○[1]²⁰ | ◆[1]²¹ | △[1]²² △[1]²³ △[1]²⁴ △[1]²⁵ | △[1]²⁶ | ○[1]²⁷ | ○[1]²⁸ |
| **T3** Structure | ◆[1]²⁹ | ○[3]³⁰ | ▲[1]³¹ △[1]³² ▲[1]³³ | ◆[1]³⁴ | △[3]³⁵ △[3]³⁶ ▲[1]³⁷ | ◆[3]³⁸ | ○[2]³⁹ |
| **T4** Synthesis | ◆[1]⁴⁰ | ○[1]⁴¹ | ▲[1]⁴² ▲[1]⁴³ | ○[1]⁴⁴ | – | ◆[3]⁴⁵ | ○[2]⁴⁶ |
| **T5** Uncertainty | ▲[1]⁴⁷ ▲[1]⁴⁸ | ○[1]⁴⁹ | ▲[1]⁵⁰ | ◆[1]⁵¹ | ▲[1]⁵² | ◆[1]⁵³ | ◆[1]⁵⁴ |
| **T6** Constrained inference | ▲[1]⁵⁵ | ○[2]⁵⁶ | ▲[2]⁵⁷ | ○[2]⁵⁸ | ○[2]⁵⁹ | ▲[2]⁶⁰ △[3]⁶¹ | ▲[2]⁶² |
| **T7** Causal estimation | – | – | – | – | △[3]⁶³ | ◆[3]⁶⁴ | ◆[3]⁶⁵ |
| **T8** Interface | ◆[1]⁶⁶ | – | ○[1]⁶⁷ | ◆[1]⁶⁸ | ○[1]⁶⁹ | ○[1]⁷⁰ | ○[2]⁷¹ |

*Key.* Entry numbers run left to right and top to bottom; each is described, with its citation, tag rationale and integration tier, in Appendix C.

Two of the 18 evaluated entries, numbers 51 and 53, record methods that are demonstrated on IO objects but fall outside the definition of AI in §2.4; they are kept so that a reader assembling an uncertainty workflow knows they exist, and are marked so that they are not counted towards the demonstrated AI base. Four patterns carry the argument.

Demonstrated entries concentrate in T1, T2 and T5 at stages S1, S3 and S4: estimation, assignment and calibration, upstream of the algebra. That is Tier 1, and it is where the field's effort appropriately sits. The evaluated ones concentrate further still: eleven of the sixteen AI entries with a reported out-of-sample evaluation sit in those three stages.

Column S2 now holds one demonstrated entry, in the form of firm-to-sector attribution inside a working MRIO, and concordance estimation has arrived at the adjacent stage. The construct choice itself is the one cell in the column where no study was located, and it determines what every downstream estimate is an estimate of.

Rows T6 and T7 have changed most. Constrained and differentiable computation was the emptiest row and now holds five demonstrated entries, four of them evaluated; causal estimation was empty and now holds one, unevaluated by construction, since its estimand is a treatment effect. One T6 entry requires care: the sensitivity of a footprint to all technical coefficients, d**L** = **L**(d**A**)**L**, is the first-order field of influence (Hewings et al., 1988; Sonis & Hewings, 1992; Dietzenbacher, 1990), and for a scalar footprint the gradient is an outer product of two vectors a standard calculation already produces. The defensible opportunities are computing the full field of influence at global MRIO scale, which enumeration has never made affordable, and differentiating through an entire compilation pipeline, which is unavailable today.

Cell T3×S5 holds the largest literature and the weakest evidence. Entry 37 stands for 21 studies that cluster or attribute drivers on already-computed footprints, of which one reports a held-out protocol. Counting entries, and not studies, keeps the map legible; counting studies would place the field's centre of gravity in that one cell, which by volume is where it is.

One cell moved in the opposite direction from the rest. T2×S5 was recorded in earlier drafts as not meaningful, on the ground that assignment has no target object where the objects are derived indicators. Weimar, Daly and Wood (2010) shows that the cells of a table can serve as the feature space for an assignment task whose target lies outside the accounts, so the combination is meaningful. It is tagged △ because the study reports no evaluation, and nothing in this review's argument rests on it.


## 8. Limitations and risks

We separate hazards documented in the IO or EEIO literature from those reasoned from mechanisms established elsewhere but not yet observed here.

### 8.1 Documented

*Uncertainty is large, structural and correlated, and has been quantified for nearly fifty years.* Analytical and Monte Carlo propagation dates to Bullard and Sebald (1977, 1988) and West (1986); MRIO results include Lenzen, Wood and Wiedmann (2010), Wilting (2012), Karstensen, Peters and Andrew (2015) and Rodrigues, Moran, Wood and Behrens (2018). The defensible claim is that uncertainty is rarely propagated into published results, not that it is unquantified. Expectation does not commute with inversion (Quandt, 1959), and accounting constraints induce strong correlation across cells (Rodrigues, 2016), which also breaks the exchangeability conformal guarantees require. Whether correlated cell errors amplify or cancel at the level of a footprint is not settled by that observation and depends on the structure of the propagation: Schulte, Jakobs and Pauliuk (2024) report that uncertainty falls substantially between emission accounts and footprints, which they attribute to cancellation across supply chains, while the same study finds sector-level dispersion in the accounts themselves to be large. Both results are theirs and both belong in any statement of this problem. Appendix H.3 sets out how their sectoral coefficients of variation should be read, including what their Dirichlet allocation prior does and does not assume.

*Transfer is assumed more often than it is tested.* Firm-network models degrade substantially when moved between countries (Mungo et al., 2023), imputation error rises sharply when a model trained on a large database is applied to a smaller one (Zhao et al., 2025), and the one conference result with cross-country validation reports errors from −38.4% to +216.1% (He et al., 2025). Against that, one new study builds a national emission extension for a country that publishes none by training on 34 Annex I inventories and transferring to a hydrocarbon economy whose electricity, desalination and refining profiles are unlike any in the training set (Alkhayat, 2026). The design is the right one to attempt and the transfer is the kind the evidence above says fails; the thesis is partly embargoed and we could not establish what out-of-sample check accompanies it. Non-transfer should remain the default assumption, and the conditions under which transfer is possible are a research problem in their own right (Pan & Yang, 2010).

*Split variance is large and almost never reported.* Random split choice alone moves reported accuracy substantially on a life-cycle inventory imputation task (Zhao et al., 2025). Four of the 62 included studies report repeated runs with dispersion: a subsampling design (Mungo et al., 2023), a study whose subject is split variance itself (Zhao et al., 2025), an ensemble average over 10³ sampled network configurations (Fessina et al., 2026), and an open benchmark reporting standard deviations over ten runs (Guo, Guan, & Ma, 2026). None of the four is an estimate of an input–output table.

*Reported figures are not comparable, and the risk is false comparability.* Appendix B states this of its own rows, and it applies with equal force to any comparison a reader might draw from §5. Label spaces, IO objects, aggregation levels, sample sizes and metrics differ. Two coefficients of determination on cell values, from different countries at different aggregation levels against different baselines, do not rank two methods. We report them side by side because that is what a map does, and we state here that the side-by-side arrangement is not a ranking.

*Reporting standards are weak enough to obstruct synthesis.* We name a study in this section when a specific, checkable feature of its reporting would mislead a reader who took its headline figure at face value; other studies with unreported fields are recorded in Appendix B without comment. Four meet that test. One team reported the same reconstruction and forecasting exercise for the same eleven provinces, seven sectors and forecast horizon in three publications, in two languages, without any of the three citing the others (Zou, Li, & Han, 2025, 2026); we counted it once and excluded two records as redundant reports. The journal article among them carries a data-availability statement declaring that no datasets were generated or analysed, in a paper whose central contribution is a reconstructed 2007 to 2024 MRIO time series, and its accuracy comparisons are presented as normalised bar charts with no numeric values. One study on the resilience of a Chinese provincial manufacturing chain appears in a journal that publishes on electromagnetics, opens with a sentence about sensing infrastructure that plays no part in its analysis, and reports a coefficient of determination computed on synthetically oversampled training data without a held-out test set (Cui & Ma, 2026); we include it, flagged, because a map of what exists should not quietly drop what it dislikes, and we would not rely on its figures. And the earliest classifier trained on IO table cells reports no accuracy figure, no baseline and no validation protocol at all (Weimar et al., 2010), which is why it is tagged △ and why nothing in this review rests on it.

*Detectability should be a reporting requirement.* An error that no available test can distinguish from a correct result is not a small error, it is an unmeasurable one. Any study proposing a learned component for compilation should state which of its plausible failure modes would be detected by the checks a compiler actually runs, and which would not. The invariance suite of §9.1 exists to make that statement possible; at present no study in our sample makes it.

*Specification and aggregation error exceed most reported improvements.* Sector aggregation moves emission multipliers materially (Steen-Olsen et al., 2014; Bouwmeester & Oosterhaven, 2013; Zhang, Caron, & Winchester, 2019), and loss of detail produces errors of the order of 80% in the forestry case examined by Lenzen and Rueda-Cantuche (2012). Any claimed improvement must be reported with the aggregation level and construct at which it was measured.

*The evidence base is concentrated, and the concentration is in one half of it.* Twenty-one of the 62 included studies use Chinese data, at national, provincial or firm level. Eighteen of those 21 are in the downstream group of §5.5; only three of the 29 studies that act on an IO object use Chinese data. We report the geography of the data rather than the affiliation of the authors, because it is the data that carry a statistical system's compilation conventions into a method calibrated on them, and Appendix B records the data scope of every study so that the count can be checked. Concentration is not a criticism of the work. Its consequence is that the downstream literature is largely a literature about one country's provincial MRIO system, while the literature on estimation is geographically dispersed and much smaller.


### 8.2 Reasoned, not yet observed in input–output work

*Circular validation.* When one model family imputes cells, flags anomalies, writes the checks and drafts the narrative, errors become self-confirming, because an imputation drawn from a model's prior appears maximally plausible to a detector drawn from the same prior. Patterns consistent with the mechanism are visible in our sample: a classification benchmark built from language-model output (§5.4), learned updaters trained on partly RAS-derived targets (§5.3), a graph architecture evaluated against ground truth generated by the identity it encodes (§5.1), and a web-trace trade predictor validated against modelled trade estimates (§5.3). No study has measured the effect in IO. Mitigation is architectural: provenance tags carried from cell to result, validation against exogenous invariants, and a requirement that imputation and validation models not share a training corpus. A geographic gradient is plausible, since uncertainty inputs already differ by income group, with national inventory uncertainties for Annex I countries and default values elsewhere (Schulte et al., 2024); we state that as a hypothesis.


*Model monoculture.* If compilers, consultancies and auditors adapt the same few foundation models, errors align instead of averaging, and independent teams cease to provide independent checks (Kleinberg & Raghavan, 2021). The model-collapse literature describes the same mechanism on the data-generating side (Shumailov et al., 2024).

*Adversarial response.* Where an estimated quantity has financial consequences, such as a customs classification or a sector assignment that determines an emission intensity, it can be influenced once the classifier is known. No accuracy figure in this literature is measured under such conditions.

*Dual use.* Reconstructed firm networks name suppliers, chokepoint analyses serve as target lists as readily as resilience assessments, and facility-level asset maps are commercial reconnaissance. At sector resolution the question did not arise; it arises now, and the field has no publication norm for it. We suggest one: where a result identifies specific firms or facilities, authors should state whether the identification is estimated or observed, and journals should require justification for publishing identifying detail in place of aggregates.

*Deskilling and assurance.* Manual capability is what makes an anomaly noticeable, and it is lost by attrition, never by decision. No assurance framework states how to sign off a figure that changes between runs.

### 8.3 Access and licensing

Access to MRIO databases is not the binding constraint on this research programme: FIGARO, the OECD inter-country tables (Yamano et al., 2023) and WIOD are freely downloadable, EXIOBASE is released under a share-alike licence, Eora is free for academic use, GLORIA requires registration, GTAP is licensed. The constraint is redistribution and derived-work terms, which leave the status of a pooled multi-database training corpus, or of a model adapted from one, unsettled. That is a narrower problem, and one the consortia can resolve directly; the shared compilation infrastructure that would carry such an agreement already exists (Lenzen et al., 2017).


## 9. Research agenda

Table 2 states eleven questions we judge important and answerable. The final column records whether each requires machine learning, is an ordinary IO or computational question that the AI literature has made urgent, or is both. Three of the eleven do not require learning, and saying so is part of the contribution.

**Table 2.** Priority research questions. Tier follows §6.3.

| # | Question | Stage / task | Tier | Why it matters | Requires AI? |
|---|---|---|---|---|---|
| Q1 | Does a metamorphic invariance suite detect failures in published learning components that accuracy metrics miss? | All / T8 | 2 | The only validation route needing no ground truth | Both |
| Q2 | Does constraint-embedded generation beat residual correction on identical real tables and identical baselines, does either beat the previous year's coefficient matrix, and is the corrected table rebalanced? | S3 / T4, T6 | 1–2 | Tests §6.2; the exhibits have never been compared, and neither the naive baseline nor the rebalancing step has been reported | AI |
| Q3 | Bródy (1997) conjectured that the subdominant eigenvalue modulus of **A** falls with matrix size, a result proved for random matrices (Sun, 2008) but not observed in the empirical statistical structure of US coefficient matrices (Torres-González & Yang, 2019). Is the low effective rank seen in practice an economic property or an artefact of biproportional construction? | S3 / T3 | 1 | Determines whether low-rank imputation applies at all | IO |
| Q4 | Can input-criticality matrices be extended by language models from documentation and procurement text, and does the extension reproduce survey-based validation performance? | S6 / T2 | 1 | The learnable object in the best-validated shock model; a benchmark exists | AI |
| Q5 | Can the full field of influence be computed at global MRIO scale, and does the resulting coefficient ranking agree with compilers' revision priorities? | S5 / T6 | 2 | Enumeration has never been affordable; the identity is not new | IO |
| Q6 | What is the conditional coverage, by region, sector and income group, of calibrated intervals on model-produced IO cells under the non-exchangeability accounting constraints induce? | S7 / T5 | 1 | Marginal coverage can conceal severe local failure | Both |
| Q7 | How large is the aggregate basic-versus-purchasers'-price error in spend-based value-chain accounting? | S4 / T1 | 1 | A large systematic error for which we located no quantification | IO |
| Q8 | For the economies that publish establishment-level make and use data, can a learned model predict which SUT-to-IOT construct best reproduces held-out establishment data? | S2 / T1 | 1 | The one empty cell of the construct column; empirically testable where the data exist | AI |
| Q9 | Do independently developed learning components exhibit correlated errors when they share a foundation model or pretraining corpus? | All / T8 | 2 | Tests whether monoculture is a real mechanism here | AI |
| Q10 | Does training gap-fillers with impact-weighted rather than cell-weighted losses reduce footprint error, and how does this relate to holistic versus partitive accuracy? | S1, S3 / T1 | 1 | Current metrics optimise a quantity users do not care about | Both |
| Q11 | Does learned concordance estimation generalise across classification pairs and vintages it was not trained on, and what is its class-balanced accuracy on the sparse off-diagonal entries that carry the information? | S4 / T2 | 1 | Concordances are the seam through which multi-source compilation passes; the first result reports unweighted accuracy only | AI |

Q8 has a constraint that should be stated rather than discovered by whoever attempts it. The test Rueda-Cantuche and ten Raa (2013) describe needs establishment-level make and use data, and the offices that publish it at the required detail are few; on our reading of the national accounts documentation this is a single-digit number of economies. That makes Q8 a well-posed estimation problem within an economy and a poorly posed generalisation problem across economies, and a study that treats a handful of national instances as a training sample would repeat the small-sample error this review criticises elsewhere. The tractable version is within-economy: predict, from establishment data held out at random, which construct reproduces it best, and report whether the answer is stable across years.


### 9.1 The invariance suite

Metamorphic testing (Chen et al., 2018) asks not whether an output is correct but whether it changes as it must under transformations whose effect is known exactly. Because IO analysis has no true table against which an estimate can be scored, and because the tables that exist are partly model output, such tests are the only validation route available that requires no ground truth.

Appendix D states each invariant formally, with its conditions, a proof, and the error class it detects. The suite comprises: invariance of physical footprints to uniform monetary rescaling; the same under sector-specific rescaling, conditional on consistent transformation of extensions; permutation equivariance, which tests the implementation unless the model consumes ordered input; linear scaling of a linear footprint under proportional scaling of final demand; a valuation-basis relation, which is the only test in the suite capable of detecting the price-basis error of §3.3; and the Leontief–Ghosh duality relation under the price-model reading (Dietzenbacher, 1997). Two candidate invariants do not hold and are excluded with reasons in Appendix D: equality of aggregate-then-compute with compute-then-aggregate, which fails because aggregation and inversion do not commute (Lenzen, 2011); and invariance to insertion of a zero-output sector, which is ill-posed because coefficients are undefined at zero output.

### 9.2 Proposals we regard as promising but untested

Appendix J records seven proposals that no located study has attempted, flagged as speculative and offered because a map listing only what exists is of limited use. They are: differentiating an entire compilation pipeline; impact-weighted losses; learning the reliability weights KRAS already accepts as inputs; active learning over survey and verification budgets; generative table synthesis under hard accounting constraints; inverse optimisation on the disruptions of 2020 to 2022; and low-rank completion over the country-by-sector-by-sector-by-year panel. Appendix J also states what an agent operating an IO model through its own interface would have to be able to do.

### 9.3 Institutional steps

Three, in order of leverage. Statistical offices should publish a provenance flag with every supply-use cell recording whether it is surveyed, administratively sourced, deterministically derived or model-imputed; it is the cheapest action available to anyone in this map, it unblocks honest uncertainty and non-circular validation, and the environmental accounting and life-cycle pedigree traditions supply the precedent. Database consortia should build the remaining missing benchmarks and settle the derived-work licensing question. Journals and funders should require deposition of code and data versions, and that claims of demonstrated application resolve to a primary source.


## 10. Conclusion

Learning methods have entered input–output analysis, and the shape of the entry is what this review reports. Sixty-two studies met our criteria, and 33 of them apply learning to numbers a conventional input–output calculation has already produced. That literature is growing quickly, is concentrated in environmental-science journals and in one country's provincial data, and continues a decomposition tradition the field already has. The 29 studies that act on an input–output object sit upstream of the algebra, which is appropriate for now, because the accounting identities bound a learned estimate's error and because every demonstrated success has retained them.

The evidence is thinner than the count suggests. Of the 71 entries in the map, 18 rest on a study that reports an out-of-sample evaluation and 20 on a study that reports none. Four studies in 62 report dispersion across runs, and none of the four estimates an input–output table. The first head-to-head comparison of a learned updater against RAS, on United Kingdom tables in 2002, ended in a tie, and no comparison since has been run on common data with common baselines.

Dispersal is the condition of this literature rather than an artefact of how we searched for it. A third of the included studies are absent from the two major citation databases; one conference contribution appeared at the Association's meetings in the years that produced twelve published studies acting on IO objects; the earliest classifier trained on IO tables reached print in a safeguards proceedings. A field cannot develop conventions it cannot see, and the absence of shared benchmarks, of reported dispersion and of a common vocabulary follows from that more than from any lack of interest.

Two commitments of IO data limit what any estimator can deliver, and neither is a data problem. The derivation of a symmetric table from supply and use tables is a modelling choice with axiomatic and empirical consequences, and no located study addresses it. The monetary unit assumes price homogeneity within sectors and biases every physical inference drawn from it. An estimator can be told which construct and which valuation basis it is estimating within; it cannot choose them, and a study that does not state them has not specified what it estimated.

The constraints that bind the wider programme are institutional. There is one open benchmark, no ground truth for the tasks that matter, licence terms that leave pooled corpora unsettled, and a validation architecture capable of confirming its own errors. The field's capacity to produce estimates is growing faster than its capacity to check them, and the second is the cheaper of the two to build.



---


# Appendices

*Appendices are exempt from the main-text word limit. Appendices A, B, C and E are additionally deposited as machine-readable supplements so that the map can be extended and corrected.*

## Appendix A. Protocol, search log and PRISMA-ScR flow

### A.1 Eligibility

*Population.* IO, MRIO or EEIO objects: transaction matrices, technical coefficient matrices, supply and use tables, concordance matrices, environmental extensions, firm-level production networks framed in or validated against the IO tradition, or indicators derived from any of these.

*Concept.* A method that fits a function or representation from data, where the functional form is learned and not specified in advance (§2.4). Prototype-based unsupervised partitioning that the primary literature labels as machine learning, principally k-means and hierarchical clustering, is admitted; classical matrix factorisation applied for the same descriptive purpose is not, and §2.6 records the consequence of that line.

*Context.* Any country, sector or production setting, research or official.

*Included publication types.* Peer-reviewed articles; conference papers with retrievable full text; agency, national-laboratory and statistical-office reports; doctoral and other theses; preprints, flagged as such in Appendix B. No quality threshold is applied at inclusion, in line with PRISMA-ScR (Tricco et al., 2018) and with the scoping-review methodology of Munn et al. (2018); appraisal is reported in Appendix B and weak reporting is discussed in §8.1 under the rule stated there.

*Excluded.* Studies applying IO analysis to the environmental footprint of AI itself (eleven records). Studies naming machine learning without applying it, including those inheriting the term from a parent project or a machine-assigned concept tag. Studies in which the learned component acts neither on an IO object nor on an IO-derived indicator. Redundant reports and earlier versions of an included study. Records that are not research outputs. Vendor material without a stated method, retained separately as deployment evidence and never supporting a demonstrated tag.

*Language.* English, with two included studies published in Chinese carrying English abstracts and metadata. *Dates.* No lower bound; last search 4 September 2026.

### A.2 Term sets

*IO terms:* "input-output analysis"; "input-output table"; "input-output tables"; "multi-regional input-output"; "multiregional input-output"; "MRIO"; "environmentally extended input-output"; "EEIO"; "supply and use table"; "supply and use tables"; "supply-use table"; "Leontief". Hyphen, en-dash and plural variants were enumerated separately because they return materially different record sets.

*AI terms:* "machine learning"; "deep learning"; "neural network"; "artificial intelligence"; "large language model"; "random forest"; "gradient boosting"; "graph neural network".

### A.3 Search log

Forty-three searches were executed between 30 August and 4 September 2026 and logged with source, verbatim query, UTC timestamp and record count. The deposited supplement carries the full log. Sources queried, with outcome:

| Source | Queries | Records returned | Outcome |
|---|---|---|---|
| Scopus | 1 | 261 | Executed 4 September 2026; all databases; no filters |
| Web of Science | 1 | 50 | Executed 4 September 2026; all databases and editions; no filters |
| OpenAlex | 1 | 197 | Executed 4 September 2026 with the same expression; 93 duplicated the two citation databases |
| Directory of Open Access Journals | 15 | counted per query | Executed; counts recorded |
| Crossref REST API | 3 | n/a | Executed; used for identifier verification, cannot express Boolean AND |
| Europe PMC | 2 | 61 residual | 19 retrieved, 42 unretrievable |
| OpenAIRE | 1 | n/a | Executed; non-Boolean |
| RePEc / IDEAS | 4 | n/a | Native search interface robots-disallowed; site-restricted web search reached the index |
| EconPapers | 2 | n/a | Reached via site-restricted web search |
| CORE, BASE, Lens.org, Dimensions, CiteSeerX | 5 | n/a | Executed or partially executed; outcomes logged individually |
| Taylor & Francis; ScienceDirect | 4 | n/a | Bot-walled; publisher site search unavailable |
| General web search, including vendor and practitioner material | 4 | n/a | Executed; one search targeted specifically at quantifications of the valuation error of §5.4, with a null result |
| Semantic Scholar Graph API | 7 attempts | 0 | HTTP 429 on every attempt across three sessions |
| EconLit; Google Scholar | 0 | n/a | Not searched; see below |

*Sources considered and not searched.* EconLit requires institutional authentication that was not available to us, and its economics coverage overlaps substantially with Scopus and RePEc for the period in which this literature is concentrated. Google Scholar has no interface permitting automated querying and its terms forbid it, and its record-level metadata is not stable enough to support a reproducible screening ledger. Aggregator platforms such as ProQuest and EBSCO were not searched separately, since they redistribute content indexed in the sources above. JSTOR was considered and set aside: it is a full-text archive rather than an abstracting service, most of its journals carry a three- to five-year moving wall, and the publishers in which this literature principally appears are not archive content.

*What the sources contribute.* The three principal sources overlap far less than their nominal coverage suggests. Scopus and Web of Science shared 33 of their 278 unique records. OpenAlex shared 93 of its 194 unique records with them, leaving 101 new, of which 10 were included. Six of those ten are grey literature the citation databases do not index. The remaining four are indexed journal articles whose input–output content sits in the methods rather than in the title, abstract or keywords. Against this, metadata quality in the open index is markedly worse: 12 of the 29 OpenAlex records taken to full assessment carried no abstract, and 20 of the 101 new records were front matter, indexes, code deposits, or duplicate preprint and published pairs.

### A.4 PRISMA-ScR flow

Every figure in this section is computed by script from the deposited ledger of Appendix I together with the carried-forward counts of the open-index round; none is transcribed.

| Stage | n |
|---|---|
| Records identified, open indexes and repositories | 162 |
| Records identified, Scopus | 261 |
| Records identified, Web of Science | 50 |
| Records identified, OpenAlex | 197 |
| **Records identified, all sources** | **670** |
| Duplicates removed, within open-index set | 15 |
| Duplicates removed, Scopus against Web of Science | 33 |
| Duplicates removed, citation-database round against open-index round | 6 |
| Duplicates removed, within OpenAlex export | 3 |
| Duplicates removed, OpenAlex against earlier rounds | 93 |
| Records after de-duplication | 520 |
| Unretrievable residual carried openly (Europe PMC) | 42 |
| Screened at title and abstract | 478 |
| Excluded at screening | 379 |
| Assessed in full | 99 |
| Excluded at full assessment | 37 |
| **Included** | **62** |
| of which learning acts on an IO object (Appendix B.1) | 29 |
| of which learning acts on IO-derived results (Appendix B.2) | 33 |
| of which boundary decisions, flagged throughout | 6 |
| Dedicated AI-for-IO reviews identified | 0 |

Screened records by round: 105 in the open-index round, 272 in the citation-database round after removing the six records shared with it, and 101 in the OpenAlex round.

Exclusion reasons at screening (total 379): non-economic sense of "input–output" 197; AI named but not applied 90; learned component acting on neither an IO object nor an IO-derived indicator 42; other 16; no retrievable full text 12; IO applied to AI's footprint, out of scope 11; not a research output 7; duplicate of an included record at a different vintage 4.

Exclusion reasons at full assessment (total 37): learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity 10; insufficient metadata after full-text retrieval was attempted 10; no learned component on inspection 8; redundant report, earlier version or data deposit of an included study 7; method outside the concept definition 1; input–output analysis applied to the economic effects of AI 1.

Exclusion reasons are single-classifier judgements.

### A.5 Growth over time

Included studies by year of publication: 1 (2000), 1 (2001), 1 (2002), 1 (2010), 1 (2016), 1 (2018), 1 (2019), 2 (2020), 0 (2021), 4 (2022), 8 (2023), 6 (2024), 9 (2025), 26 (2026 to 4 September).

Three features matter. The prehistory is sparse rather than absent: five studies between 2000 and 2016, separated by gaps of seven and five years, and none cited by the current wave. The 2010 study reports no evaluation and reached print in a nuclear materials management proceedings, so the capability existed and its result is unknown. And the acceleration from 2022 is driven by the downstream group of §5.5: of the 53 studies published from 2022 onward, 30 apply learning to results a conventional IO calculation has already produced. Appendix E shows no corresponding rise in the conference record before 2026.

### A.6 Queries as executed

Scopus, Advanced Search, 4 September 2026, all databases, no filters:

`TITLE-ABS-KEY(("input-output analysis" OR "input-output table*" OR "multi-regional input-output" OR MRIO OR "environmentally extended input-output" OR EEIO OR "supply and use table*" OR Leontief) AND ("machine learning" OR "deep learning" OR "neural network*" OR "artificial intelligence" OR "large language model*" OR "random forest*" OR "gradient boosting" OR "graph neural network*"))`

Web of Science, Advanced Search, 4 September 2026, all databases and editions, no filters: the same expression in the `TS=` field. OpenAlex, 4 September 2026: the same expression, executed against its search index and exported in full.

Returned 261, 50 and 197 records respectively. The 472 unique records from the three sources account for 46 of the 62 included studies.

### A.7 Comparator syntheses

Two near-miss reviews were retrieved and read. Gong et al. (2025) is a bibliometric review of 1,068 publications at the industrial-ecology and AI intersection; input–output analysis is not identified as an adopting subfield. Mensikova et al. (2026) reviews 209 full texts on AI in life-cycle assessment; the strings "input-output", "MRIO", "EEIO" and "Leontief" do not occur in it. Neither is a substitute for the present review, and neither claims to be. Our own search history indicates why they missed the field: most of the relevant studies are in journal families those reviews do cover, and a third of them are not in the citation databases at all.


## Appendix B. Study-level evidence table

### B.0 What this table can and cannot support

Sixty-two included studies, split by what the learned method acts on. B.1 covers the 29 studies in which learning acts on an input–output object and appraises each on fourteen fields. B.2 covers the 33 in which learning acts on quantities a conventional input–output calculation has already produced; those are appraised on eight fields, because the remaining six are unreported in almost every case.

Three properties of the table govern what may be inferred from it. Reported accuracy figures are **not** comparable across rows, since label spaces, IO objects, aggregation levels, sample sizes and metrics differ; the rows are a record, not a ranking, and §8.1 restates this. Fields recorded as *not reported* are a finding about the literature rather than a gap in our extraction. And fields recorded as *not retrievable* mean the publisher blocked access to the full text or the work is embargoed; 18 of the 62 studies have at least one such field, and five of the 29 in B.1 report no evaluation metric of any kind.

The consequence is that this table documents the reporting practices of the literature more reliably than it documents the performance of the methods. That is the use we make of it: the tag scheme of §7 distinguishes studies that report an out-of-sample evaluation from those that do not, and the counts in §8.1 are counts of reporting, not of quality.
### B.1 Learning acts on an input–output object (29 studies)

| Citation | Inferential task | IO object acted on | Data / geographic scope | Sample size | Baseline | Metric(s) reported | Split protocol | Repeated splits & dispersion | Uncertainty reported | Code available | Data available | Peer-reviewed | Independently replicated |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Wang (2001), *Neural Computing & Applications* 10(1) | T3 (structural substitution) | Proposed as an alternative to the Leontief solution mapping | China, stated as motivation; scope not retrievable | Not retrievable | Classical Leontief IO analysis, conceptually | Not retrievable | Not reported | N | N | N | N | Y | N |
| Papadas & Hutchinson (2002), *Applied Economics* 34(13) | T1 (estimation) | Technical coefficient matrix and derived multipliers | United Kingdom IO tables | Not retrievable | **RAS**, on the same tables | Directional only in accessible text; **RAS more accurate overall**, many individual forecasts better from the network | Successive table years, not a random split | N | N | N | N | Y | N |
| Weimar, Daly & Wood (2010), INMM 51st Annual Meeting (PNNL-SA-73279) | T2 (assignment) | Cells of national IO transaction tables used as the feature space | 37 OECD member and associate countries, 1993–2005; 48 ISIC Rev. 3 sectors, 2,304 cells per table | 93 country-year tables | None reported | "High probability" of correct assignment; no confusion matrix, AUC or out-of-bag error reported | Not reported | N | N | N | N | **N** (conference proceedings, national-laboratory report) | N |
| Pakizeh & Kashani (2022), *Spatial Economic Analysis* 17(2) | T1 (estimation, regional coefficients and multipliers) | Regional input-coefficient matrix | Japan, multiple regions as training donors | Not retrievable | Location-quotient models | "Superior performance" vs. LQ; figures not retrievable | Not reported | N | N | N | N | Y | N |
| Zhao, Shuai, Qu & Xu (2022), *Environ. Sci. Technol.* 56(16) | T1 + T6 (RAS-embedded correction) | US summary-level technical coefficient matrix | United States national IO tables | Not reported | RAS alone | R² 0.6412→0.8726 (1yr), 0.5271→0.7893 (5yr); median APE 37.49%→11.35% (1yr), 51.12%→18.26% (5yr) | Not reported | N | N | Not reported | Not reported | Y | N |
| Potashnikov (2022), Zenodo preprint | T1 (estimation, table updating) | Direct-cost (technical coefficient) matrix | Russia; sector count and years not retrievable | Not retrievable | **RAS, GRAS and cross-entropy**, named in the abstract as the methods the approach is intended to replace | Not retrievable (full text in Russian; deposit could not be opened) | Not retrievable | Not reported | Not reported | N | N | **N** (preprint) | N |
| Mungo, Lafond, Astudillo-Estévez & Farmer (2023), *J. Econ. Dyn. Control* 148 | T2 (link prediction) | Firm-to-firm transaction network | Compustat (US, 915 firms/1,033 links), FactSet (global, 6,714/40,861), Ecuador (10,000/587,693) | As above | Sales-driven max-entropy; gravity (logistic); ERGM | AUC > 0.9 across all 3 datasets | 70:30, 5 subsampled datasets per undersampling ratio | **Y** (mean ± SD across 5 subsamples) | Partial | Not reported | Partial | Y | N (within-paper transfer degrades substantially) |
| Tranos, Carrascal-Incera & Willis (2023), *Ann. Am. Assoc. Geogr.* 113(3) | T1 (estimation of interregional trade flows) | Interregional trade block of a regional supply-use system | United Kingdom, NUTS2 regions and local authorities, 15 sectors, 2000–2010 | Region-pair-sector-year observations; count not retrievable | Distance-only specification; no formal gravity benchmark confirmed | R² > 0.9 across test years; 2002: R² 0.96, RMSE 937.93, MAE 159.87 | **Rolling forecast**: train on years *t*, *t*+1, predict *t*+2; 10-fold CV within training | Partial (nine test years, no dispersion statistic) | N | Not confirmed | Partial (web archive open; no replication deposit found) | Y | N |
| Cullen, Marinoni & Cullen (2024), *J. Ind. Ecol.* 28(4) | T1 (gap-filling) | GHG emissions database records (EEIO extension) | 3 GHG datasets of increasing complexity | Not reported (18 gap-filling methods tested) | Tree ensembles, graph methods, interpolation, compared to each other | ~97% (missing time steps) and 60–70% (missing emitters); metric definition not retrievable | Not retrievable | Not reported | Not reported | Y (Zenodo) | Y | Y | N |
| Dumit et al. (2024), NeurIPS Workshop | T2 (classification / spend coding) | EEIO sector classification (295 BEA-derived classes) | US, synthetic company spend line items | 10,000 synthetic items generated by a language model | 4 baseline models (unnamed in accessible text) | 57.3% top-1, 72.2% top-3 | Not reported | N | N | N | Partial ("on request") | **N** (workshop paper) | N |
| Guo, Qian, Credit & Ma (2025), arXiv:2502.06874 (GREEN) | T2 (hierarchical classification) | EEIO/NAICS crosswalk (ExioNAICS) | North America, 20,850 companies, 1,114 NAICS categories | As above; 20-company emission case study | Not confirmed beyond "state of the art" | 83.68% top-1, 91.47% top-10; MAPE 45.88% (case study) | Not reported | Not reported | Theoretical bound claimed | Y (HuggingFace) | Y | **N** (preprint) | N |
| Fukui (2025), *Computational Economics* 65(4) | T1 + T4 (mixup synthesis) | Regional input-coefficient matrix | Japan: 42 prefectures + 4 cities (train), 3 cities held out; 12 sectors | 50,000 synthetic regions: 40,000 train / 10,000 test | FLQ and variants; RAS; Papadas & Hutchinson (2002) ANN | STPE 0.0434 vs 0.0679–0.3527; RMSE 0.0035 vs 0.0056–0.0292 | 80/20 within synthetic pool + 3 held-out cities | N (min/mean/max, not CIs) | N | Not reported | Y | Y | N |
| Zhao, Jiang, Xu & Tu (2025), *J. Ind. Ecol.* 29 | T1 (diagnostic study of estimation instability) | LCA unit-process inventory records (EEIO-adjacent) | Ecoinvent 3.1; US LCI (transfer test) | Full databases | Diagnostic, not benchmarked | Qualitative: split randomness and database size affect stability; magnitude not retrievable | Studies split randomness as its subject | **Y** (by design) | Not reported | Not reported | Partial | Y | N |
| Mudiyansege, Kumari, Pepper, McDowell & De Zoysa (2025), AIC IEOM 2025 | T2 (classification / spend coding) | Scope 3 category and emission-factor assignment for ledger transactions | Organisational general-ledger expenditure records | Not retrievable | Manual mapping (the incumbent practice) | Not retrievable | Not retrievable | Not reported | Not reported | Not reported | Not reported | Y (conference proceedings) | N |
| Hou et al. (2025), *Scientific Data* 12(1) | T2 (firm-to-sector attribution) feeding T1 (compilation) | Intermediate transaction matrix of a coupling MRIO, via firm-to-sector attribution; balanced by GRAS | China (30 provinces, 30 sectors) and 66 economies; 2017; >2 million trade records | Classifier corpus size not disclosed | Manual annotation for the classifier; EXIOBASE, OECD ICIO, CEADs for the table | Classifier accuracy 0.96; import/export deviation vs. customs 2.53% / 5.09% (EXIOBASE 17.82% / 16.16%; OECD 11.82% / 11.12%) | **Not reported** for the classifier | N | N (three imputation scenarios, no error propagation) | Y (figshare) | Y (figshare) | Y | N |
| Fessina et al. (2026), *Sci. Rep.* 16 | T3 (network reconstruction) | Firm-level production network from sector-level data | Ecuador, VAT records 2008 | 29,089 firms, 371 sectors, 130,044 links | DCGM, IOGM, SCMM | Economic Systemic Risk Index; centrality; correlation vs. empirical network | Full-network reconstruction vs. complete ground truth | **Y** (10³ sampled configurations) | Partial (ensemble dispersion) | Not reported | N (confidential VAT data) | Y | N |
| Yu, Wang, Manya & Hsu (2026), *Sci. Data* | T1 + T5 | Subnational GHG inventories (EEIO extension vectors) | G20: 5,972 cities + 116 regions, 2000–2020 | 9,664 self-reported entries | EDGAR; Data Portal for Cities; GRACED | R² 0.77; MAPE 38.57% | 80/20 single split (managed internal CV) | Partial | **Y** (95% PI, 94.5% empirical coverage) | Y | Y (UNC Dataverse) | Y | N |
| Guo, Guan & Ma (2026), *Sci. Data* 13(1) (ExioML) | T1 (estimation of an environmental extension) | Sector-level factor accounts and footprint edge lists derived from EXIOBASE 3.8.2; the released task predicts sectoral greenhouse-gas emissions | 49 regions, 28 years, 1995–2022; product-by-product (200) and industry-by-industry (163) variants | Full released tables | **Yes**: ridge and k-nearest neighbours as shallow baselines against tree ensembles and deep tabular models | Mean squared error; best model ≈ 0.19–0.20 against ridge ≈ 2.3–2.5 in the precursor release | **64:16:20, fixed before tuning** | **Y** (ten repeated runs with standard deviations) | N | **Y** (GitHub) | **Y** (Zenodo) | Y | N |
| Kim, Choi & Hong (2026), *Building and Environment* 303 | T3 (structure) + T1 (forecast) | Annual US IO tables as weighted graphs; forecasts of the Leontief inverse | United States, BEA tables 1997–2024, 71 industries | 28 annual graphs | Not retrievable | Scenario results reported (163.22 tCO2e per $1m construction demand, 2027 baseline); predictive error not retrievable | Not retrievable | Not reported | Not reported | Not reported | Not reported | Y | N |
| Köse et al. (2026), arXiv:2605.15842 | T2 / T3 (LLM link classification + reconstruction) | Firm-level supply, partnership and ownership network, validated against OECD ICIO and BACI | Global semiconductor industry, 170M webpages | 999 firms / 3,407 edges (core) | S&P Capital IQ; OECD ICIO; BACI | Precision 0.884 / F1 0.784 (binary); precision 0.918 / F1 0.758 (multi-class); country-level *r* ≈ 0.61–0.64 | Not reported | Not reported | Not reported | Not reported | Not reported | **N** (preprint) | N |
| De Pretis, Tortoli & Caria (2026), *Sci. Rep.* 16 | T4 + T6 (constrained generative estimation) | National (NIOT) and world (WIOT) IO tables, 56×56 | 43 countries (NIOT); 15 world tables (WIOT) | NIOT 35 train / 8 test; WIOT 12 train / 3 test | Improved RAS | R² 0.9417 vs 0.8524 (NIOT); R² 0.9972 (WIOT); diagonal correlation 0.8228 vs 0.3165 | Single fixed split | N | N (named as future work) | Y | Partial | Y | N |
| Fukui (2026), arXiv:2603.13823 | T1 (estimation) + T6 (balancing) | Regional input–output table, estimated item by item then balanced | Japan, 2015 national table as benchmark | Not reported | **Matrix balancing under known row and column sums**, an idealised upper bound | "Generally higher estimation accuracy" than the idealised balancing benchmark; per-item figures not reported in the abstract | Not reported | N | N | Not reported | Y (public sources) | **N** (preprint) | N |
| Alkhayat (2026), doctoral thesis, King Abdullah University of Science and Technology | T1 (estimation of an environmental extension) | Industry-resolved national greenhouse-gas extension (ISIC Rev. 4) | Trained on 34 Annex I countries, 2008–2021 (UNFCCC inventories, World Development Indicators, OECD Air Emissions Accounts); transferred to Saudi Arabia | 34 countries × 14 years | Global emission-factor databases calibrated to foreign sectoral profiles | Not retrievable | Not retrievable | Not retrievable | Not retrievable | Not retrievable | Partial (public sources listed) | **N** (thesis) | N |
| Pattanavekin & Ekgasit (2026), Research Square preprint | T1 (estimation) + T5 (calibration) | Spend-normalised monetary emission intensity, the EEIO intensity coefficient | Thailand, cement and concrete products; procurement graph over electronic tax records | 132 registry-verified footprints in 7 supplier cliques; 42 fitting, 90 blinded test | **Static Thai EEIO 2021 factors; EXIOBASE MRIO 2022** | RMSE 0.185 → 0.042 kg CO₂e/THB against the static EEIO baseline; 95.2% empirical coverage against a 90% nominal target | **Blinded held-out test set of 90 observations, sequestered until final evaluation** | N | **Y** (split-conformal calibration) | Not reported | N | **N** (preprint) | N |
| Fazal, Ma, Baynes & Lenzen (2026), *Economic Systems Research* 38(3) | T2 (assignment) | **Concordance matrices** | Classification pairs not retrievable | Not retrievable | Manual construction (labour comparison); no algorithmic baseline retrievable | "Up to 85% accuracy"; class balance not stated | **Not retrievable** | Not reported | Not reported | Not retrievable | Not retrievable | Y | N |
| Zheng et al. (2026), *Proc. SPIE* 14142 | T3 + T1 (sector output prediction) | Inter-sectoral coefficient structure, as a graph | Not retrievable (empirical application, country not stated) | Not retrievable | Random forest, XGBoost, GCN, GraphSAGE; **no linear IO baseline** | "Lower error" than four learned baselines; figures not retrievable | Not retrievable | Not reported | Not reported | N | N | Y (conference proceedings) | N |
| Zhang et al. (2026), *Front. Energy Res.* 14 | T1 + T6 (constrained imputation) | Firm-level technical coefficient matrix and Scope 3 extension; Leontief propagation as architecture | **Synthetic**: 2,000-node scale-free network; robustness on ER, WS variants | 2,000 nodes; MNAR missingness | Mean imputation; KNN; random forest; label propagation; **GraphSAGE ablation**; RF + topology oracle | RMSE 144.41 (proposed) vs 172.31 (ablation), 267.75 (RF), 89.14 (oracle) | Single fixed MNAR split, seed 42 | **N** (single seed) | **Y** (MC dropout, 100 passes; 90% PI width 7.01) | N | N (synthetic, regenerable) | Y | N |
| Benhari, Kaicer & Driss (2026), *Stat. Optim. Inf. Comput.* 15(2) | T6 (learned solver) | Interval-valued **A** and the solution of (**I** − **A**)**x** = **f** | **Synthetic**: Monte Carlo interval systems, *n* = 2, 3, 5, 10; 6-sector Leontief illustration | 10,000 samples per system | Gauss elimination, Gauss–Jordan, Jacobi, Gauss–Seidel | MAE 0.055–0.242; R² > 0.97; Hausdorff 0.109–0.604; **coverage 1–25% before calibration, ~90% after** | Train/validation split, proportions not disclosed | N | **Y** (interval outputs, coverage-calibrated) | N | N (example reproducible from printed matrices) | Y | N |
| Wang, Zheng, Chen, Hu & Ouyang (2026), *Ecosystem Services* 77, **boundary decision** | T1 (estimation) | Biophysical flood-mitigation capacity, entering a SEEA ecosystem supply-use table after routing and valuation | Wanquanhe Basin, Hainan, China; 2020 | Not retrievable | None reported | None reported for the random forest | Not reported | N | N | N | N | Y | N |

*Notes on B.1.* Two studies (Zhang et al.; Benhari et al.) evaluate on synthetic data only, and in the first the synthetic ground truth is generated by the identity the architecture encodes. Two are preprints. One (Dumit et al.) is a workshop paper. Nine carry at least one field marked *not retrievable*. Three report dispersion across repeated runs, and none of those three is an estimate of an input–output table. The single most consistent absence is a naive baseline: no study in this table reports the previous year's coefficient matrix or a growth extrapolation as a comparator.

### B.2 Learning acts on results a conventional IO calculation has produced (33 studies)

Thirty-three studies. "IO step" names the conventional calculation that produces the learned model's input or target. Predictive metrics are reported only where the study frames a prediction task; most do not.

| Citation | IO step | Learned method | What is learned | Baseline reported | Predictive metric | Split protocol | Note |
|---|---|---|---|---|---|---|---|
| Ito (2000), *Kybernetes* 29(9/10) | Dynamic IO system gives controlled sectoral outputs under an optimal control policy | Neural network, architecture unspecified | Sectoral output trajectories and projections to 2010 | None reported | None reported | Not applicable (in-sample control simulation) | Japan, 3 aggregate sectors, 9 annual observations; earliest included study |
| Liu, Moreno & García (2016), *Energy* 115 | Sectoral shares from a national IO table allocate a forecast total | BP network combining three grey models | Aggregate primary energy consumption | Not retrievable | Not retrievable | Not reported | Earliest instance of the forecast-then-allocate template |
| Saliminezhad & Lisaniler (2018), *J. Int. Trade Econ. Dev.* 27(5) | IO linkages identify high-linkage sectors | MLP; ant-colony feature ranking | Relation between engine sectors and GDP growth | Multiple linear regression | Reported qualitatively (nonlinear model "outperforms") | Not reported | Indonesia, 1995–2015 |
| Chen, Zhu, Wiedmann, Yao, Xu & Wang (2019), *Applied Energy* 250 | Provincial MRIO gives per-capita household energy requirements | Decision tree, random forest, XGBoost | Energy-requirement class from survey attributes | **Yes** (decision tree vs. ensembles; also OLS) | **Accuracy 68.71% / 89.39% / 89.46%; κ 0.858, 0.819** | **80:20 with 5-fold CV** | Best-reported study in B.2; 25,661 households, 25 provinces |
| Abdella, Kucukvar, Onat, Al-Yafay & Bulak (2020), *J. Clean. Prod.* 251 | EIO-LCA sustainability impacts of US food sectors | k-means; logistic regression | Sustainability performance class | Not retrievable | Model accuracy 91.67% | Not retrievable | Full text not retrievable |
| Wang & Zhou (2020), *J. Intell. Fuzzy Syst.* 39(6), **boundary decision** | Intermediate input decomposed from IO tables | Genetic-algorithm-tuned BP network | Drivers of financial-sector development | Not reported | Not reported | Not reported | Method description insufficient to verify |
| Pang & Kong (2022), IEEE ICET 2022 | MRIO + CFPS gives household carbon emissions | Lasso-XGBoost; SP-LIME | Household carbon emissions from attributes | Decision tree | Accuracy 90.5% (urban), 91.2% (rural) | Not reported | Imbalance handled by oversampling |
| Ma, Liu, Li, Zhang & Fang (2023), *Environ. Sci. Pollut. Res.* 30(15) | Ecologically extended IO gives virtual-water flows | BP network | Sectoral water consumption under scenarios | Not reported | Not reported | Not reported | Kazakhstan; scenario range, not predictive uncertainty |
| Zhou, Li, Ding, Huang & Shen (2023), *J. Clean. Prod.* 389 | IO model gives sectoral carbon emissions | Bayesian neural network | Emission paths to 2050 | Not reported | Not reported | Not reported | Guangdong |
| Zhi et al. (2023), *Process Saf. Environ. Prot.* 175 | MRIO gives interregional virtual water | k-means; structural decomposition | Regional groupings | Not applicable | Not applicable | Not applicable | 8 regions, 17 sectors, 2012 and 2017 |
| Liu, Liang, Xu & Ye (2023), *Sustainability* 15(12) | MRIO gives embodied carbon in provincial trade | k-means | Three provincial clusters | Not applicable | Not applicable | Not applicable | China |
| Fang, Cheng, You, Chen & Peng (2023), *Sustainability* 15(23) | EE-MRIO gives mineral resource footprints | Random forest | Driver importance | Not reported | Not reported | Not reported | Monte Carlo used for model reliability, not UQ on the footprint |
| Konstantakis et al. (2023), *Ann. Oper. Res.* 327(2), **boundary decision** | IO mapping traces the US food supply chain | Neural terms augmenting an ARDL model | Production-process relation | ARDL without NN terms | Not retrievable | Not retrievable | Learned component auxiliary to an econometric model |
| Han, Tang & Liu (2024), *Resour. Environ. Yangtze Basin* 33(10) | MRIO gives an intercity carbon-transfer network | Random forest regression | Effect of integration on transfer | OLS | Not reported | Not reported | Published in Chinese |
| Wang et al. (2024), *J. Clean. Prod.* 475 | MRIO gives economy-water interactions | CNN-LSTM with factorial design | Water consumption under SSPs | Not reported | Not reported | Not reported | Inner Mongolia, Shaanxi, Ningxia |
| Li, Liu, Yuan & Lu (2024), *Energy Sources B* 19(1) | MRIO gives embodied carbon in steel trade | Bat-optimised extreme learning machine | Embodied carbon intensity 2026–2034 | Not reported | Not reported | Not reported | CBAM scenario study |
| Li, Zhang, Hu & Zuo (2024), ACM CAIBDA 2024 | IO table plus RAS gives a cascade-propagation model | DDPG reinforcement learning, adaptive variant | Intervention policy minimising cost | Standard DDPG | Convergence and accuracy claimed, no figures | Not applicable | Only reinforcement-learning application located |
| Jin & Zhang (2025), *PLOS ONE* | Ghosh supply-side model | LSTM | Time-varying multipliers | Static Ghosh model | Not reported | Not applicable | China, marine sectors, 2017–2023 |
| Faridzad (2025), *J. Econ. Struct.* 14(1), **boundary decision** | OECD IO tables give linkages | Clustering with PCA; centrality scores | Key-industry groupings | Traditional linkage measures | Not reported | Not applicable | Australia, 4 years |
| Liu, Liang, Zhou, Xu, Ye & Liu (2025), *ACS Sustain. Chem. Eng.* 13(24) | MRIO gives six-dimensional resource flows | Clustering | Three regional clusters and a sustainability index | Not applicable | Not applicable | Not applicable | 30 Chinese regions |
| Huo, Bian, He & Lv (2025), *Digit. Econ. Sustain. Dev.* 3(1) | Interprovincial IO tables give a domestic value-chain resilience indicator | Gradient boosting inside a double machine-learning estimator | Causal effect of digital-real economy integration on chain resilience | Conventional econometric specifications | Not reported as predictive accuracy (the estimand is a treatment effect) | Cross-fitting within the double-ML design | China, 2012, 2015 and 2017 tables; the only debiased-learning study acting on an IO-derived outcome |
| Faridzad (2026), *Asian Development Review* 43(1) | Demand- and supply-driven IO gives four linkage indices | Hybrid k-means and hierarchical clustering | Sector groupings by financial interdependence | Traditional linkage measures | Not reported | Not applicable | Malaysia, 2022, robustness 2018–2021 |
| Ge, Qu, Huang et al. (2026), *Energy Economics* 158 | IO-supported accounting gives household carbon emissions | Tree ensembles with importance attribution | Driver importance | OLS run alongside | Not reported | Not reported | 5,585 households, 108 cities |
| Ge, Yan, Guo & Zhang (2026), *Energy Strategy Rev.* 64 | EEIO gives embodied carbon of power infrastructure | Random forest | Emissions to 2060 under three scenarios | Not reported | Not reported | Not reported | Fujian |
| Zhao & He (2026a), *Transp. Res. E* 207 | EE-MRIO gives maritime embodied carbon flows | MLP with SHAP; exponential random graph model | Driver importance; network formation | Not reported | "High precision" claimed, no figure | Not reported | 2000–2020 |
| Zhao & He (2026b), *Transport Policy* 179 | EE-MRIO gives bilateral transport carbon transfers | CatBoost with Bayesian tuning, SHAP; hierarchical clustering | Driver importance; pathway classes | Not reported | Not reported | Not reported | 64 nations, 2000–2018 |
| Li, Li, Huang, Wang, Liu, Xu & Li (2026), *J. Clean. Prod.* 560 | IO analysis gives virtual-water transfers | CNN-LSTM with attention | Water supply and demand under SSP-RCP | Not reported | Not reported | Not reported | Arid region, upper Yellow River |
| Li, Li, Huang, Wang & Li (2026), *Environ. Sci. Eng.* | IO analysis gives virtual-water sources | CNN-LSTM | Water consumption | **LSTM** | R² > 0.9 | Not reported | Ningxia; likely overlaps the preceding entry |
| Zou, Li & Han (2026), *Netw. Spat. Econ.* 26(2) | RAS with cross-entropy reconstructs missing MRIO years | Whale-optimised **grey** neural network; GRA, QAP, SHAP | Carbon footprints and transfers to 2030 | PSO-GM, GA-BP, linear regression, ARIMA (in the companion report) | Presented as normalised bar charts; **no numeric values** | Not reported | Counted once; two companion reports excluded as redundant |
| Liu (2026), *AIP Advances* 16(7), **boundary decision** | Enterprise-level MRIO supplies firm variables | System dynamics coupled with machine learning | Enterprise performance under policy scenarios | Not reported | Not reported | Not reported | Method description insufficient to verify the learned step |
| Cui & Ma (2026), *Adv. Electromagn.* 15(3), **boundary decision** | 2020 Shandong IO table parameterises a CGE model and weights an industry network | Random forest with SMOTE oversampling; Gini and Shapley attribution | Resilience index under 5–15% tariff shocks | **None reported** | R² 0.83, RMSE 0.04, on synthetically oversampled data | Tenfold cross-validation for tuning; no held-out test set | 28 industries, 588 observations expanded to 1,000 by oversampling. Venue publishes on electromagnetics; see §8.1 |
| Zhu, Yang & Li (2026), *Environ. Sci. Pollut. Res.* | Environmentally extended input–output LCA gives life-cycle carbon emissions | XGBoost with SHAP and SHAP-based piecewise regression | Non-linear thresholds in life-cycle emissions | Not reported | Not reported | Not reported | Single reservoir case study, China; the coupling between the Monte Carlo EEIO output and the XGBoost design matrix is not retrievable |
| Yin, Zhao, Fu, Pereira, Meadows, Ding & Liu (2026), *Nature Sustainability* 9(6) | Eora26 MRIO gives virtual water, energy and food flows | Random forest, confirmed from the methodological citation and the code deposit | Not retrievable | Not reported | Not reported | Not reported | Global, country level. Methods paywalled; the learned component appears in neither the abstract nor the figure captions. Not returned by either citation database, since the IO content sits in the methods |

*Notes on B.2.* Six of the thirty-three report an alternative predictive model as a baseline; a further six compare against a conventional non-learned method such as ordinary least squares, a static Ghosh model or a traditional linkage measure. Two report a train–test protocol. None reports repeated runs with dispersion. Twenty-one compute a footprint or embodied-flow result with a conventional MRIO calculation and then apply a learned model to that result. The learned step here does not touch the accounts, so these studies bear on consumption patterns and not on whether learning can improve an input–output account; §5.5 situates them against the structural decomposition tradition they extend. We include them because omitting them would misstate the size and direction of the field's activity.


## Appendix C. The map, cell by cell

Seventy-one entries across fifty-six cells, generated together with Table 1 from one source list. For each: the entry as numbered in the key to Table 1, the evidence tag, the integration tier, the citation or the explicit record that no study was located, and the rationale for the tag. Where the tag is *demonstrated in IO*, the learning paradigm (D1) and inductive bias (D2) are given. Entries are classified by the inferential target of the published claim, not by the method used.

| # | Cell | Tag | Tier | Source or absence | Rationale; learning paradigm and inductive bias where demonstrated |
|---|---|---|---|---|---|
| 1 | T1×S1 | ▲ | 1 | Yu et al. (2026); Guo, Guan and Ma (2026) | Ensemble regression estimates unobserved subnational emission totals on an 80:20 split; ExioML defines a sectoral emission-estimation task on EE-MRIO-derived accounts with a 64:16:20 split fixed before tuning and ten repeated runs. Supervised / tabular ensembles and deep tabular models |
| 2 | T1×S1 | △ | 1 | Cullen et al. (2024) | Systematic comparison of eighteen learned gap-fillers on emissions databases; accuracies reported, split protocol and metric definition not retrievable. Supervised / mixed |
| 3 | T1×S1 | ▲ | 1 | Zhang et al. (2026) | Missing firm-level Scope 3 emissions imputed on a directed supplier graph, single fixed split, six baselines, ablation. Supervised / message-passing network. Synthetic ground truth generated by the Leontief identity the architecture encodes |
| 4 | T1×S1 | △ | 1 | Alkhayat (2026) | Multi-output tree ensembles trained on 34 Annex I inventories construct an industry-resolved national emission extension for a country that publishes none. Supervised / tabular ensemble. Doctoral thesis, partly embargoed; no evaluation retrievable |
| 5 | T1×S1 | ▲ | 1 | Pattanavekin and Ekgasit (2026) | Monetary emission intensities predicted from a procurement graph, evaluated on a blinded test set of 90 observations against static national EEIO factors and against EXIOBASE. Supervised / graph attention. Preprint; 42 fitting observations in 7 cliques |
| 6 | T1×S2 | △ | 1 | Wang, Zheng, Chen, Hu and Ouyang (2026); boundary decision | Random forest estimates biophysical capacity that, after routing and valuation, populates a SEEA ecosystem supply-use table. No evaluation reported. Two deterministic steps separate the learned and tabulated quantities |
| 7 | T1×S2 | ○ | 1 | No study located under the search of Appendix A | Construct selection from establishment data is testable (Rueda-Cantuche and ten Raa, 2013) but unattempted; §9 states how many economies could supply instances |
| 8 | T1×S3 | ▲ | 1 | Zhao et al. (2022) | Learned residual correction to a RAS estimate, evaluated one and five years ahead on tables not used in fitting. Supervised / feed-forward network |
| 9 | T1×S3 | ▲ | 1 | Fukui (2025) | Regional coefficients estimated with synthetic augmentation, 80:20 within the augmented pool plus three held-out cities. Supervised / feed-forward network |
| 10 | T1×S3 | △ | 1 | Fukui (2026) | Per-item deep learning followed by matrix balancing, benchmarked against balancing with known margins; per-item figures not reported. Same author as the preceding entry, so not independent corroboration |
| 11 | T1×S3 | △ | 1 | Pakizeh and Kashani (2022); Papadas and Hutchinson (2002) | Learned regional and national coefficients compared with location-quotient formulae and with RAS. Figures not retrievable for either. In the 2002 comparison RAS was more accurate overall by a margin the authors call too small to be systematic |
| 12 | T1×S3 | △ | 1 | Potashnikov (2022) | Convolutional networks forecast the direct-cost coefficient matrix using published sectoral forecasts in place of the intermediate-demand data RAS requires. Preprint in Russian; accuracy figures not retrievable |
| 13 | T1×S4 | ◆ | 1 | No IO study located under the search of Appendix A; method established in price-index and margin estimation | Valuation conversion is a regression problem, unattempted on EEIO intensities |
| 14 | T1×S5 | △ | 1 | Li, Liu, Yuan and Lu (2024); Ge, Yan, Guo and Zhang (2026); Zou, Li and Han (2026) | Forecasting of embodied carbon intensities and footprints computed by a conventional MRIO calculation. No baseline and no split protocol reported in any of the three |
| 15 | T1×S6 | △ | 1 | Kim, Choi and Hong (2026) | Annual IO tables represented as graphs and the Leontief inverse forecast forward; downstream computation unchanged. Predictive error not retrievable |
| 16 | T1×S6 | △ | 3 | Jin and Zhang (2025) | Recurrent network supplies time-varying multipliers in a Ghosh model; no train-test structure. Tier 3: substitutes for model structure |
| 17 | T1×S7 | ○ | 1 | No study located under the search of Appendix A | Imputation of missing validation series |
| 18 | T2×S1 | ◆ | 1 | No evaluated IO application located under the search of Appendix A; method established in information extraction | Extraction of inventory values from documents; the characteristic failure is a wrong boundary or unit |
| 19 | T2×S2 | △ | 1 | Hou et al. (2025) | Retrieval plus a fine-tuned language model attribute firms to sectors inside a compiled MRIO; balancing by GRAS. Reported accuracy 0.96 with no corpus size and no split protocol disclosed |
| 20 | T2×S2 | ○ | 1 | No study located under the search of Appendix A | Allocation of establishment output to product classes |
| 21 | T2×S3 | ◆ | 1 | No IO application located under the search of Appendix A; donor selection is established in survey imputation | Donor selection for disaggregation |
| 22 | T2×S4 | △ | 1 | Fazal, Ma, Baynes and Lenzen (2026) | Concordance matrices predicted from textual sector labels, up to 85% accuracy. Class balance and split protocol not stated; concordances are sparse binary objects, so an unweighted accuracy can be high on the zeros alone |
| 23 | T2×S4 | △ | 1 | Dumit et al. (2024) | Expenditure to EEIO sector, 295 classes, 57.3% top-1. Split protocol not reported; benchmark items synthetic |
| 24 | T2×S4 | △ | 1 | Guo, Qian, Credit and Ma (2025) | Company description to industry class, hierarchical retrieval, 83.7% top-1. Split protocol not reported |
| 25 | T2×S4 | △ | 1 | Balaji et al. (2023); Mudiyansege et al. (2025) | Product to sector without task-specific training, about 48%; and ledger transactions to Scope 3 categories against manual mapping, figures not retrievable |
| 26 | T2×S5 | △ | 1 | Weimar, Daly and Wood (2010) | Random forest discriminates a country attribute from a selected subset of the 2,304 cells of national IO tables, on 93 country-year tables. No accuracy figure, no baseline and no validation protocol are reported, so the result is unknown. The features are table cells and the target lies outside the accounts; §7 states why the cell is nonetheless meaningful |
| 27 | T2×S6 | ○ | 1 | No study located under the search of Appendix A | Event coding for shock vectors |
| 28 | T2×S7 | ○ | 1 | No study located under the search of Appendix A | Concordance conflict detection |
| 29 | T3×S1 | ◆ | 1 | Trase (2026), agency material without peer-reviewed evaluation | Asset detection from imagery; tagged adjacent, not demonstrated, per §2.4 |
| 30 | T3×S2 | ○ | 3 | No study located under the search of Appendix A | Bipartite product-by-industry representations (Appendix F.3, R4) |
| 31 | T3×S3 | ▲ | 1 | Fessina et al. (2026) | Firm network reconstructed from sector tables and validated against a complete national network, averaged over 10³ sampled configurations. Unsupervised, maximum entropy / graph |
| 32 | T3×S3 | △ | 1 | Köse et al. (2026) | Temporal multi-relational firm networks from unstructured text; precision and F1 reported, split protocol not reported. Preprint |
| 33 | T3×S3 | ▲ | 1 | Tranos, Carrascal-Incera and Willis (2023) | Interregional trade flows predicted from web hyperlink traces in a rolling design with cross-validation inside each training window. Supervised / tabular ensemble. The ground truth is itself a modelled estimate |
| 34 | T3×S4 | ◆ | 1 | No IO application located beyond the concordance entry above; method established in schema matching | Embedding-based crosswalks between arbitrary classifications |
| 35 | T3×S5 | △ | 3 | Kim et al. (2026); Zheng et al. (2026) | Graph propagation substituted for the linear IO mapping in footprint and sensitivity analysis. Neither reports an evaluation against the linear model it replaces |
| 36 | T3×S5 | △ | 3 | Jin and Zhang (2025) | Structural paths in a learned supply-side model |
| 37 | T3×S5 | ▲ | 1 | Twenty-one studies; see Appendix B.2 | Clustering and driver attribution on footprints already computed by a conventional MRIO calculation. One of the twenty-one reports a held-out protocol with cross-validation (Chen et al., 2019); the other twenty report none, which is why the tag records the best case and not the typical one. Tier 1 because the accounts are untouched |
| 38 | T3×S6 | ◆ | 3 | No IO application located under the search of Appendix A; established in firm-level supply-chain learning | Learned production functions |
| 39 | T3×S7 | ○ | 2 | No study located under the search of Appendix A | Learned aggregation for reporting |
| 40 | T4×S1 | ◆ | 1 | No IO application located under the search of Appendix A; established in statistical disclosure control | Synthetic microdata |
| 41 | T4×S2 | ○ | 1 | No study located under the search of Appendix A | Synthetic SUTs under construct constraints |
| 42 | T4×S3 | ▲ | 1 | De Pretis et al. (2026) | Generative estimation with an iterative proportional fitting step inside the generator, single fixed split. Adversarial / generative plus constraint layer |
| 43 | T4×S3 | ▲ | 1 | Fukui (2025) | Virtual regions synthesised by interpolation between observed regions to enlarge a small training set. Supervised / data augmentation |
| 44 | T4×S4 | ○ | 1 | Dumit et al. (2024) uses synthetic ledgers as data, not as a released benchmark resource | A real-ledger benchmark does not exist |
| 45 | T4×S6 | ◆ | 3 | Furtado and Andreão (2022), agent-based rather than IO | Emulated scenario ensembles |
| 46 | T4×S7 | ○ | 2 | No study located under the search of Appendix A | Synthetic corruption for detector testing |
| 47 | T5×S1 | ▲ | 1 | Yu et al. (2026) | Prediction intervals with reported empirical coverage on estimated extension cells. Supervised / ensemble |
| 48 | T5×S1 | ▲ | 1 | Zhang et al. (2026); Pattanavekin and Ekgasit (2026) | Monte Carlo dropout intervals on imputed firm emissions, with reported width; and split-conformal calibration on learned intensities, 95.2% empirical coverage against a 90% nominal target on 90 blinded points. §5.7 states why that coverage figure is weakly informative at this sample size and dependence structure |
| 49 | T5×S2 | ○ | 1 | No study located under the search of Appendix A | Construct-choice uncertainty |
| 50 | T5×S3 | ▲ | 1 | Rodrigues (2014); Tsionas (2020) | Posterior inference over table cells. Tagged demonstrated in IO for the estimation task; the methods are Bayesian statistics, not learning, and the tag records IO applicability, not AI content |
| 51 | T5×S4 | ◆ | 1 | No application to automated coding located under the search of Appendix A; Angelopoulos and Bates (2023) for the method | Conformal triage of automated coding. The one conformal application located acts on estimated intensities, not on classification decisions |
| 52 | T5×S5 | ▲ | 1 | Schulte et al. (2024) | Monte Carlo propagation on IO objects. As with the balancing entry above, the method is not AI under §2.4; the tag records IO applicability |
| 53 | T5×S6 | ◆ | 1 | No IO application located under the search of Appendix A; established in macroeconomic forecasting | Density nowcasts |
| 54 | T5×S7 | ◆ | 1 | No IO application located under the search of Appendix A; established in Bayesian workflow | Posterior predictive checks on tables |
| 55 | T6×S1 | ▲ | 1 | Zhang et al. (2026) | Input-injection residual connections encode the Leontief series inside a message-passing architecture; ablation isolates the device, raising root mean squared error from 144 to 172 when removed. Synthetic data |
| 56 | T6×S2 | ○ | 2 | No study located under the search of Appendix A | Differentiable construct transformation |
| 57 | T6×S3 | ▲ | 2 | De Pretis et al. (2026); Fukui (2026) | Balancing operator inside or after a learned model, in one case differentiated through and in the other applied to predicted cell values |
| 58 | T6×S4 | ○ | 2 | No study located under the search of Appendix A | Differentiable concordance |
| 59 | T6×S5 | ○ | 2 | Identity known since Hewings et al. (1988); no MRIO-scale computation located under the search of Appendix A | Field of influence at global scale |
| 60 | T6×S6 | ▲ | 2 | Alleman et al. (2023) | Calibration of a dynamic shock model against four independent series |
| 61 | T6×S6 | △ | 3 | Li, Zhang, Hu and Zuo (2024) | Policy learning over a cascade model built on an IO table and balanced by RAS; the only reinforcement-learning application located. No figures reported. Tier 3: the policy replaces the modelled response |
| 62 | T6×S7 | ▲ | 2 | Benhari, Kaicer and Driss (2026) | Network trained to return interval solutions of (**I** − **A**)**x** = **f**, benchmarked against four classical solvers; empirical coverage 1–25% before post-hoc width calibration and about 90% after. Synthetic, six sectors |
| 63 | T7×S5 | △ | 3 | Huo, Bian, He and Lv (2025) | Gradient boosting supplies the nuisance functions of a double machine-learning estimator whose outcome is a value-chain resilience indicator computed from interprovincial IO tables. The estimand is a treatment effect, so no predictive metric applies; identification rests on the design and not on the accounts |
| 64 | T7×S6 | ◆ | 3 | No IO application located under the search of Appendix A; established in policy evaluation | Ex-post evaluation feeding IO parameters |
| 65 | T7×S7 | ◆ | 3 | No IO application located under the search of Appendix A; method established | Disciplining causal language in IO reporting |
| 66 | T8×S1 | ◆ | 1 | No evaluated IO application located under the search of Appendix A; established in retrieval-augmented generation | Retrieval over methodology documents. Hou et al. (2025) uses retrieval as a compilation step, tagged at the assignment entry above |
| 67 | T8×S3 | ○ | 1 | No study located under the search of Appendix A | Agent-assisted compilation audit |
| 68 | T8×S4 | ◆ | 1 | No IO application located under the search of Appendix A; established in assisted annotation | Assisted concordance review |
| 69 | T8×S5 | ○ | 1 | No study located under the search of Appendix A | Agents operating an IO model through its interface; §9.2 sets out what such an agent would have to be able to do |
| 70 | T8×S6 | ○ | 1 | No study located under the search of Appendix A | Scenario interfaces |
| 71 | T8×S7 | ○ | 2 | No study located under the search of Appendix A | Automated invariance harnesses (§9.1) |

Cells marked "–" in Table 1 are T4×S5, T7×S1, T7×S2, T7×S3, T7×S4 and T8×S2. Each is recorded as not meaningful for a stated reason: synthesis has no target object at the structural-analysis stage, where the objects are derived indicators rather than records; causal estimation requires an identification strategy that compilation, construct choice, balancing and classification do not admit, since these are estimation problems with no counterfactual; and interface work has no object at the construct stage.

Two cells that earlier drafts of this map recorded as not meaningful are now occupied, and both changes are stated here because a map whose empty cells cannot be falsified is not doing any work. T6×S1 was excluded on the ground that constrained inference precedes any accounting constraint at the source-data stage; entry 56 shows that a Leontief-derived architectural constraint can be imposed on an extension-estimation problem. T2×S5 was excluded on the ground that assignment has no target object where the objects are derived indicators; entry 26 shows that the cells of a table can serve as the feature space for an assignment task whose target lies outside the accounts, and it is tagged △ because that study reports no evaluation.

Thirty-eight entries carry a demonstrated tag, 18 of them with a reported out-of-sample evaluation. Excluding entries 51 and 53, which record non-AI methods, 36 entries are demonstrated AI applications, of which 16 are evaluated. They rest on 29 distinct studies, of which 19 act on a core IO object, meaning a transaction or coefficient matrix, a concordance matrix, or a regional or firm-level counterpart of one; the remainder act on environmental extensions, classifications or derived networks. Entry 37 alone stands for 21 further studies whose learned components act on results rather than accounts.


## Appendix D. The invariance suite

Metamorphic testing evaluates a component against transformations whose effect on the output is known exactly, and so requires no ground truth. Let **A** be a technical coefficient matrix, **f** final demand, **L** = (**I** − **A**)⁻¹, **s** a row vector of direct intensities per unit of output, and *F* = **s L f** a scalar footprint. Let *g* denote the component under test, which may be an imputer, an updater, a classifier or an entire pipeline.

**D1. Invariance to uniform monetary rescaling.** *Statement.* Multiply every monetary entry by α > 0. Then **A** is unchanged and *F* is unchanged. *Proof.* **A** = **Z** diag(**x**)⁻¹, and both **Z** and **x** scale by α, so α cancels. *Condition.* Intensities **s** must be expressed per unit of monetary output and rescaled by α⁻¹. *Detects.* Deflator and unit-conversion errors; a learned component that has absorbed the price level of its training vintage.

**D2. Invariance to sector-specific rescaling.** *Statement.* Rescale sector *j*'s monetary units by α_j > 0. Then **A** → diag(**α**) **A** diag(**α**)⁻¹ and *F* is unchanged provided **s** → **s** diag(**α**)⁻¹. *Proof.* The similarity transform leaves the Neumann series invariant under the compensating transformation of **s**. *Detects.* Price-basis confusion within a learned component; failure of a component to propagate a unit change through both the coefficient matrix and the extension.

**D3. Permutation equivariance.** *Statement.* For any permutation matrix **P**, replacing **A** by **PAP**ᵀ, **f** by **Pf** and **s** by **sP**ᵀ leaves *F* unchanged and permutes all sectoral results by **P**. *Detects.* Implementation errors, and learned dependence on sector ordering where a model consumes ordered input. Where the model is order-invariant by construction this tests the implementation only, and the test should be reported as such.

**D4. Linearity in final demand.** *Statement.* For β > 0, replacing **f** by β**f** multiplies *F* by β. *Detects.* Nonlinear leakage in a component that should be linear; hidden clipping, saturation or normalisation.

**D5. Valuation-basis relation.** *Statement.* Let **e**_p be expenditure in purchasers' prices and **M** the published margin and tax matrices. Converting to basic prices and applying basic-price intensities must change the computed footprint by exactly the margin and tax share implied by **M**. *Detects.* The error of §3.3. This is the only test in the suite that can detect it, because D1 and D2 rescale both sides consistently and are therefore blind to it. *Condition.* Published margin and tax matrices for the economy and year in question.

**D6. Leontief–Ghosh consistency.** *Statement.* Under the price-model reading of the Ghosh formulation (Dietzenbacher, 1997), the Leontief quantity model and the Ghosh price model must yield mutually consistent results on the relations where both are defined. *Detects.* Inconsistency between quantity and price representations in a component that touches both. *Condition.* The Ghosh model must be read as a price model; the supply-driven quantity reading is not defensible (Oosterhaven, 1988, 2012).

**Two candidates that do not hold.** Equality of aggregate-then-compute with compute-then-aggregate fails, because aggregation and inversion do not commute and the residual is aggregation bias (Lenzen, 2011). Deployed as a test it would flag correct implementations as failures. Invariance to insertion of a zero-output sector is ill-posed, because technical coefficients are undefined when output is zero.

**Use.** A component passing D1 to D6 is structurally sane, not correct. The suite detects a class of error that accuracy metrics cannot see and is silent about everything else. Its value is that it costs nothing to run and requires no labels, which makes it applicable to the retrospective evaluation of published components as well as to new ones.


## Appendix E. Conference screening

Twelve meetings of the International Input-Output Association, 2014 to 2026, screened against papers tables and, where available, books of abstracts. Papers-table entries and book-of-abstracts entries are different denominators and are reported separately. Screening was conducted in multiple passes, and every candidate was verified by opening its full text or abstract, because single-pass metadata screening proved unreliable in both directions. Sources: the Association's conference pages, accessed 3 September 2026.

| Conference | Year | City, country | Papers table | Book of abstracts | AI/ML, broad | AI/ML, strict |
|---|---|---|---|---|---|---|
| 22nd | 2014 | Lisbon, Portugal | 308 | not available | 0 | 0 |
| 23rd | 2015 | Mexico City, Mexico | 239 | not available | 0 | 0 |
| 24th | 2016 | Seoul, South Korea | 280 | not available | 0 | 0 |
| 25th | 2017 | Atlantic City, United States | 230 | not available | 0 | 0 |
| 26th | 2018 | Juiz de Fora, Brazil | 150 | not verifiable | 0 | 0 |
| 27th | 2019 | Glasgow, United Kingdom | 272 | not found | 0 | 0 |
| 28th | 2022 | Langkawi, Malaysia | 100 | not verifiable | 0 | 0 |
| 29th | 2023 | Alghero, Italy | 251 | 224 | 1 | 0 |
| 30th | 2024 | Santiago, Chile | 218 | 193 | 0 | 0 |
| 31st | 2025 | Malé, Maldives | 152 | 147 | 1 | 1 |
| 32nd | 2026 | Seville, Spain | 261 | ~345 | 7 | 4 |
| **2014–2017** | | | **1,057** | | **0** | **0** |
| **2018–2025** | | | **1,143** | | **2 (0.17%)** | **1 (0.09%)** |
| **2026** | | | **261** | ~345 | **7 (2.7%)** | **4 (1.5%)** |

*Broad* counts any contribution invoking an AI or machine-learning method. *Strict* counts contributions applying a learning method to an IO object under the definition in §2.4. No meeting was held in 2020 or 2021. The Association's working paper series, which ran from 2008 to 2011, carries no AI or machine-learning item.

One 2018 contribution carries "machine learning" in its title and implements a deterministic mapping with no learning component; it is excluded from both counts, and we record it because it would otherwise constitute the earliest datum in the series and would misdate the inflection by seven years.

The 2014–2017 extension was undertaken to test whether 2018 is an arbitrary baseline. It is not: 1,057 further catalogued papers contain no AI or machine-learning contribution.

These figures must be read against the published record, and the comparison should be disaggregated before it is used. Over the 2018 to 2025 window the searches of Appendix A returned 31 included studies against two conference contributions. Of those 31, 19 are in the downstream group of Appendix B.2 and 12 act on an IO object. Restricting both sides to work that acts on an IO object gives one conference contribution against twelve published studies. The strict comparison is the fairer one and the looser one is the more commonly quoted, so we give both.

Three readings of the gap are available and we cannot fully separate them. The published literature may lie largely outside the Association's membership, which the authorship of the studies in Appendix B.2 supports. Conference programmes may under-report method when the substantive contribution is an application. And the Association's screening denominators are titles and abstracts, which are shorter than the records the databases index. What the comparison establishes is that a member relying on the conference programme to judge this literature in 2025 would have concluded that almost nothing existed. The 2026 programme, with seven contributions and a plenary session, is the first year in which the two records point the same way, and its contributions include work on learned prediction of economic aggregates at finer spatial and sectoral resolution than official statistics provide (Moran & Belaid, 2026).


## Appendix F. Glossary of methods and abbreviations

### F.1 Methods

*Supervised learning.* Fitting a function from inputs to outputs by minimising a loss on labelled examples, with the functional form learned and not specified in advance (Hastie, Tibshirani, & Friedman, 2009). Data regime: labelled examples, ideally thousands.

*Tree ensembles.* Averaging or boosting many decision trees. Random forests average trees fitted to bootstrap samples (Breiman, 2001); gradient boosting fits trees sequentially to residuals (Friedman, 2001; Chen & Guestrin, 2016). The strongest default on tabular data at the sample sizes IO offers.

*Neural network.* A composition of linear maps and nonlinearities whose parameters are fitted by gradient descent (LeCun, Bengio, & Hinton, 2015; Goodfellow, Bengio, & Courville, 2016).

*Graph neural network.* A network operating by message passing, in which each node repeatedly aggregates information from its neighbours, so that after *k* rounds a node's representation reflects everything within *k* steps (Gilmer et al., 2017; Kipf & Welling, 2017). Variants relevant here: simplified graph convolution, which removes the nonlinearities to leave a fixed polynomial in a normalised adjacency matrix (Wu et al., 2019); personalised-PageRank propagation, which uses a geometrically weighted infinite sum with a teleport probability (Klicpera et al., 2019); and implicit graph networks, which define the representation as a fixed point (Gu et al., 2020).

*Self-supervised learning.* Training on a task constructed from unlabelled data, such as predicting a masked portion of an input. The paradigm behind foundation models. Data regime: large unlabelled corpora.

*Unsupervised partitioning.* Grouping observations without labels. *k*-means fits *k* prototype vectors by alternating assignment and update (Lloyd, 1982); hierarchical clustering builds a nested partition by successive merging. Both have a fixed functional form, and we admit them because the primary literature that uses them describes them as machine learning; §2.6 records the consequence of drawing that line differently.

*Reinforcement learning.* Fitting a policy that maps states to actions by interacting with an environment and receiving rewards. Deep deterministic policy gradient is an actor-critic algorithm for continuous action spaces (Lillicrap et al., 2016). Data regime: a simulator, or a model of the environment, since real interaction is rarely available.

*Shapley additive explanations.* A post-hoc attribution of a prediction to its input features using the Shapley value from cooperative game theory (Lundberg & Lee, 2017). It explains a model, not a mechanism, and is not a causal statement about the system the model was fitted to.

*Grey model and grey neural network.* A grey model, GM(1,1), fits a first-order differential equation to a short, smoothed series and is a fixed-form extrapolator rather than a learned function; a grey neural network combines such a model with a fitted network. The abbreviation "GNN" is used for both grey and graph neural networks in this literature, and the two share nothing.

*Metaheuristic optimisation.* Population-based search over a parameter space, including particle swarm and the whale optimisation algorithm. It tunes a learned model's hyperparameters; it is not itself learning.

*Extreme learning machine.* A single-hidden-layer network whose input weights are drawn at random and whose output weights are solved in closed form.

*Mixup.* Data augmentation by convex combination of pairs of training examples and their targets (Zhang, Cissé, Dauphin, & Lopez-Paz, 2018). Applied to regional tables, the interpolation between two regions is read as a virtual region.

*Iterative proportional fitting.* Alternating row and column scaling to match margins, identical in operation to RAS and differentiable, so it can be placed inside a network's forward pass.

*Monte Carlo dropout.* Retaining dropout at prediction time and treating the resulting ensemble of forward passes as an approximate posterior (Gal & Ghahramani, 2016). It is a cheap approximation and not a calibrated interval, and its coverage must be checked empirically; modern networks are systematically miscalibrated without an explicit correction (Guo, Pleiss, Sun, & Weinberger, 2017).

*How IO propagation differs from graph-network propagation.* Three differences bear on any transfer of architecture from the graph-learning literature to IO, and §6.1 relies on them. The coefficient matrix **A** is directed and unnormalised, whereas graph convolution operates on a symmetrically renormalised adjacency matrix with self-loops added, which changes the spectrum and therefore the convergence behaviour. The entries of **A** are economically meaningful coefficients with an accounting interpretation, not free parameters. And the Leontief operator has no learned weight matrix and no nonlinearity, so the correspondence with an implicit graph network holds only for the fixed-point structure and not for the learned map applied at each step.

*Self-supervision and the small-sample constraint.* The observation that a global MRIO amounts to one network observed some twenty-five times is a statement about labelled observations. Objectives constructed from unlabelled auxiliary data, such as trade records, business registers or firm descriptions, do not enlarge the number of labelled tables but change what can be learned before a table is ever seen, which is why the two studies exploiting it (Köse et al., 2026; Hou et al., 2025) reach scales the labelled record would not support.

*Generative adversarial network.* Two networks trained in opposition, one generating samples and one discriminating them from real data (Goodfellow et al., 2014).

*Large language model.* A sequence model trained on text, typically with a transformer architecture (Vaswani et al., 2017) and self-supervised pretraining, capable of few-shot task performance (Brown et al., 2020).

*Retrieval-augmented generation.* Grounding a language model's output in retrieved documents rather than in its parameters (Lewis et al., 2020).

*Zero-shot and few-shot.* Performing a task with no task-specific training examples, or with a handful supplied at inference time.

*Top-1 and top-k accuracy.* The share of cases for which the correct class is the model's first choice, or appears among its first *k* choices. Top-3 accuracy matters where a human reviews a shortlist.

*Conformal prediction.* Attaching prediction intervals to any predictor using a held-out calibration set, without distributional assumptions (Vovk et al., 2005; Angelopoulos & Bates, 2023). Requires exchangeability; the guarantee is marginal, and distribution-free conditional coverage is impossible in the non-trivial sense (Barber et al., 2021).

*Exchangeability.* The property that the joint distribution of a sequence is invariant to reordering. Weaker than independence, and violated by IO panels.

*Physics-informed neural network.* A network trained with known governing equations added to the loss as penalty terms, so the equations hold approximately (Raissi et al., 2019).

*Projection or optimisation layer.* A network component that solves a constrained problem in the forward pass, so that stated constraints hold exactly (Amos & Kolter, 2017; Agrawal et al., 2019; Donti et al., 2021; Chen et al., 2024).

*Automatic differentiation.* Computing exact derivatives of a program with respect to all its inputs at roughly the cost of one evaluation (Griewank & Walther, 2008; Baydin et al., 2018).

*Sinkhorn iteration.* Alternating row and column scaling to match margins, equivalent to RAS, and differentiable (Sinkhorn & Knopp, 1967; Cuturi, 2013). The equivalence holds for non-negative matrices and fails for negatives.

*Emulator or surrogate.* A cheap statistical approximation of an expensive simulator, fitted to a designed set of runs.

*Split protocol; repeated splits; dispersion.* How data are divided into training and evaluation sets; whether the division is repeated; and whether variation across repetitions is reported. Omitting the last makes a single accuracy figure uninterpretable (Kapoor & Narayanan, 2023).

*Leakage.* Information from the evaluation set influencing training, producing optimistic accuracy that does not survive deployment (Kapoor & Narayanan, 2023).

### F.3 Input–output propagation and graph-network propagation

Equation (1) of §6.1 expands the Leontief inverse as a series of powers of **A**, each term propagating demand one step further along a directed weighted graph. Message passing in a graph network has the same shape. The correspondence is exact enough to be useful and inexact in three respects, and both facts matter.

*Where it is inexact.* The coefficient matrix **A** is directed and unnormalised, whereas graph convolution operates on a symmetrically renormalised adjacency matrix with self-loops added, which changes the spectrum and therefore the convergence behaviour (Kipf & Welling, 2017; Wu et al., 2019). The entries of **A** are economically meaningful coefficients with an accounting interpretation, not free parameters. And the Leontief operator has no learned weight matrix and no nonlinearity, so the correspondence with an implicit graph network (Gu, Chang, Zhu, Sojoudi, & El Ghaoui, 2020) holds for the fixed-point structure, since **L** solves **L** = **I** + **AL**, and not for the learned map applied at each step. Personalised-PageRank propagation sits between the two, applying a geometrically weighted infinite sum of powers of a normalised operator with a teleport probability guaranteeing convergence (Klicpera, Bojchevski, & Günnemann, 2019).

*What follows from it.* Two things. First, the relaxations available to a model-level proposal are enumerable, and §6.1 lists them as R1 to R4. Second, and more concretely, a graph network truncated at *k* layers computes the same object as structural path analysis truncated at path length *k*: the sum over walks of length at most *k* through the production network. Structural path analysis has a developed literature on which paths matter and how to extract them without enumerating all of them (Defourny & Thorbecke, 1984; Lenzen, 2003; Wood & Lenzen, 2009), including best-first extraction with a cut-off on path value. That literature answers, for the IO case, the question a graph-learning practitioner asks as a hyperparameter: how deep should propagation go. The answer is not a fixed number of layers but a cut-off on path contribution, and a model that adopts it inherits an interpretable stopping rule instead of a tuned one. We are not aware of any study that has made this connection, and we record it as a proposal rather than a result.

### F.4 Sub-tasks covered by the eight inferential tasks

T1 estimation of unobserved quantities: gap-filling, imputation, nowcasting, downscaling, non-survey regionalisation. T2 assignment and matching: classification, auto-coding, concordance construction, entity resolution. T3 structure and representation discovery: embeddings, clustering, community detection, network reconstruction, factorisation. T4 density modelling and synthesis: table generation, synthetic microdata, disclosure control, data augmentation. T5 uncertainty quantification and calibration: predictive intervals, conformal methods, posterior inference, coverage assessment. T6 constrained inference, optimisation and differentiable computation: projection and optimisation layers, differentiable pipelines, learned solvers, policy learning under constraints. T7 causal estimation: identification, debiased and double machine learning, ex-post evaluation. T8 interface, orchestration and verification: retrieval over documentation, assisted review, agent operation of a model, automated invariance harnesses.

### F.2 Abbreviations

AI, artificial intelligence. ARDL, autoregressive distributed lag. CV, coefficient of variation. EEIO, environmentally-extended input–output. GRAS, generalised RAS. IIOA, International Input-Output Association. IO, input–output. IOT, input–output table. KRAS, RAS under conflicting constraints. LSTM, long short-term memory (a recurrent network). MRIO, multi-regional input–output. ONS, Office for National Statistics. PRISMA-ScR, Preferred Reporting Items for Systematic reviews and Meta-Analyses, extension for Scoping Reviews. RAS, biproportional updating. SUT, supply and use table. UNECE, United Nations Economic Commission for Europe.


## Appendix G. Disclosure of generative-AI use

**Scope of use.** The evidence synthesis underlying this review was produced with substantial assistance from large language models. Model assistance was used for: literature identification and initial screening; extraction of study characteristics into the appraisal fields of Appendix B; drafting of summaries subsequently rewritten by the authors; and cross-comparison of the synthesis against independently generated syntheses of the same question produced by other systems.

**Human verification.** Every claim adopted into the manuscript was resolved to a primary source and read by the authors. Every reference in the list was checked against Crossref, a publisher record or a repository record. Every evidence tag in Appendix C was assigned or confirmed by the authors against the definition in §2.4. The conference screening of Appendix E was verified by opening each candidate contribution.

**Errors detected and corrected during preparation.** We record these because the review's own subject is the reliability of AI-assisted scholarship, and because a record of detected errors is more informative than a claim of their absence.

At the first stage, three substantive claims were adopted from model-assisted synthesis and later found to be false: an invariance relation that does not hold, because aggregation and inversion do not commute; an assertion that the identity d**L** = **L**(d**A**)**L** had no published application, when it is the first-order field of influence published in 1988; and an assertion that the spectral structure of coefficient matrices had not been studied, when it has a literature beginning with Bródy (1997). All three were detected by expert review and corrected.

At the second stage, four further errors were detected. A reference to a review of AI in life-cycle assessment did not exist; a fabricated variant, carrying a real identifier with an incorrect title and author list, had entered the reference list alongside the genuine entry and survived one round of checking. Three rows of the conference table carried transcription errors, including a wrong host city and a denominator that omitted an entire meeting. A quantitative claim about construct choice misattributed figures that the source reports for aggregation. And an empirical claim about eigenvalue behaviour was stated without its citation. All are corrected in this version; the conference table has been rebuilt from source and extended backwards by four meetings, and the reference list has been reconciled entry by entry.

At the third stage, the two bibliographic databases that earlier rounds could not reach were searched, and the results falsified three claims that had survived every previous check. The included set grew from sixteen studies to fifty-two. A statement that no learning had been applied to supply-use compilation was wrong: a published multi-regional database uses language models for firm-to-sector attribution, and a study in this journal estimates concordance matrices. A statement that the literature begins around 2021 was wrong by nineteen years: a backpropagation network was benchmarked against RAS in 2002, and the review had already cited that paper as a baseline in another study's appraisal row without recognising it as an included study in its own right. And a statement that no reinforcement-learning or learned-solver application existed was wrong in both parts. None of these errors originated in model assistance; they originated in a search that could not reach the two indexes where most of this literature sits, and they were stated in the manuscript as absences with the search behind them declared. That is the correct way to be wrong, and it is not a substitute for being right.

At the fourth stage, an open bibliographic index was searched with the same expression, and it added ten further studies, three claims among the corrections. The historical claim stated one stage earlier, that the literature begins in 2000 and then falls silent for fourteen years, was wrong in its second half: a random forest trained on the cells of national input–output tables was presented in 2010, to a meeting of the Institute of Nuclear Materials Management. The assertion that conformal prediction had no application in this field was wrong. And the assertion that no learned method had been used for causal estimation on an IO-derived quantity was wrong. Each of the three was a claim of absence, each was stated with the search behind it declared, and each fell to a source the previous search had not reached. That is now twice in successive rounds, and the pattern is not incidental to this review's subject: the strongest claims a scoping review makes are its negative ones, they are the claims most sensitive to search architecture, and this literature is dispersed across venues, languages and document types in a way that makes any single index an inadequate basis for them. We state the remaining absences with that record in view.

At the fourth stage, an open bibliographic index was searched with the same expression and added ten further studies, three corrections among them. The claim that the literature falls silent between 2002 and 2016 was wrong: a random forest trained on the cells of national input–output tables was presented in 2010, to a meeting of the Institute of Nuclear Materials Management. The claim that conformal prediction had no application in this field was wrong. And the claim that no learned method had been used for causal estimation on an IO-derived quantity was wrong.

### G.4 What this record implies, and where the risk now lies

Six claims of absence have fallen across two rounds of searching, each stated with the search behind it declared, and each falsified by a source the preceding search had not reached. Two conclusions follow and we act on both. The first is that this review states no unqualified absence anywhere: the form of words is *no study located under the search of Appendix A*, and §2.6 says what it means. The second is that we owe the reader our own estimate of where the remaining risk sits, since we are better placed than a referee to judge it. Three negative claims are most exposed.

The construct-choice claim of §5.2 is the most prominent and the most likely to fall, because the sub-problem is well defined, the data exist in a few economies, and a compiler could attempt it without publishing in a venue our search would reach. The valuation claim of §5.4 is next: we searched vendor and practitioner material specifically for a quantification and found none, but that literature is poorly indexed and commercially motivated to keep such figures internal. And the claim that no learned anomaly detection has been published on coefficient matrices is exposed for a different reason: statistical offices do this kind of work in internal documentation that is not indexed anywhere, and Appendix A.3 records that we could not search that channel systematically.

We also record one error that this round corrected. The response letter accompanying the third revision stated that the empirical premise of research question Q3 had been supported with five citations. It had not; the premise appeared in Table 2 with no citation and four of the five sources were absent from the reference list. The claim in that letter described an intention that was not carried out, and the referees were right to treat a claim of verification as a claim requiring verification. Q3 now carries three citations we have checked against publisher records, and the two we could not verify to the standard this review applies have been dropped rather than added.

**Procedural change.** Following the second-stage detections, three controls were added: every reference is now verified against an authoritative record before entering the list, and duplicates sharing an identifier are flagged automatically; every numeric claim is traced to a quoted sentence in the source; and every table is recomputed from its source record rather than transcribed. Following the third stage, one further control applies: no claim of absence is stated without the search behind it named in the same sentence or in the appendix the sentence points to.


**What this record implies.** The failure mode is consistent: fluent, plausible, specific, and wrong in ways that only domain knowledge or source-checking detects. It is the mechanism described in §8.2, and it occurred in the preparation of a review that identifies it. We regard the disclosure as part of the contribution.


## Appendix H. Supplementary background

### H.0 The four commitments in full

§3 states four commitments of IO data in the compressed form the argument requires. This section gives them in full.

*Fixed coefficients.* The identity **x** = **Ax** + **f** is definitional given a transactions table. The assumption that converts it into a model is that the coefficients in **A** are invariant to the perturbation being modelled, with constant returns and no substitution (Leontief, 1936, 1941; Miller & Blair, 2022; ten Raa, 2005). Learning can improve an estimate of **A**; it cannot establish invariance, and estimation accuracy is no substitute for that.

*The construct, in detail.* Four constructs combine a technology assumption with a sales-structure assumption. Kop Jansen and ten Raa (1990) evaluate the product-by-product constructs against material balance, financial balance, price invariance and scale invariance, and product technology alone satisfies all four. Rueda-Cantuche and ten Raa (2009) conduct the corresponding exercise for industry-by-industry constructs and find for the fixed industry sales structure; ten Raa and Rueda-Cantuche (2003) extend the axiomatic treatment, and Rueda-Cantuche and ten Raa (2013) derive econometric tests on establishment data. Product technology generates negative coefficients wherever a product is made with materially different technologies in different industries, wherever classification does not align with technology, and wherever measurement error is large relative to a cell; ten Raa and Rueda-Cantuche (2013) review the remedies, Almon (2000) develops a construction avoiding negatives, and de Mesnard (2011) argues that inverting the supply matrix is unsound on structural grounds independent of negatives. Negatives restrict the admissible estimator class, since relative-entropy methods are undefined on negative cells, which is why GRAS exists (Junius & Oosterhaven, 2003), was corrected (Lenzen, Wood, & Gallego, 2007; Temurshoev, Miller, & Bouwmeester, 2013) and was generalised to inconsistent constraints as KRAS (Lenzen, Gallego, & Wood, 2009). Formulations that keep the rectangular structure and allow an industry to operate several technologies at once are available (Duchin & Levine, 2011, 2012), as is a generalised make-and-use allocation framework shared with life-cycle assessment (Suh, Weidema, Schmidt, & Heijungs, 2010; Majeau-Bettez, Wood, & Strømman, 2014). The relevance to learning methods is that these are not data-cleaning steps: a learned estimator produces an estimate of some object, and which object is fixed by the construct.

*Aggregation, in detail.* Aggregation and inversion do not commute, and the residual is aggregation bias, which is not sign-definite (Lenzen, 2011; Bouwmeester & Oosterhaven, 2013; Steen-Olsen, Owen, Hertwich, & Lenzen, 2014; Zhang, Caron, & Winchester, 2019). It interacts with regionalisation, so that the error from using a national coefficient matrix for a region and the error from aggregating sectors are not separable (Lahr & Stevens, 2002). The magnitudes are large: Lenzen and Rueda-Cantuche (2012) report errors from loss of detail of 16% for corn and of the order of 80% for forestry, the latter because energy-intensive wood-charcoal operations are aggregated into a single forestry product. Lenzen (2011) further shows that disaggregating with fragmentary proxy data typically outperforms aggregating the environmental data, which bears directly on any learned disaggregation proposal. Two implications follow: an accuracy statistic computed at one aggregation level does not transfer to another, and an invariance test built on aggregation must be stated at the level of the indicator rather than the model.

### H.1 The supply-use to input–output transformation

Supply and use tables record, respectively, which industries make which products and which industries use which products. A symmetric table requires an assumption linking the two. Four constructs are standard, combining a technology assumption with a sales-structure assumption: product technology with fixed product sales; product technology with fixed industry sales; industry technology with fixed product sales; industry technology with fixed industry sales. The first yields a product-by-product table, the last an industry-by-industry table.

Kop Jansen and ten Raa (1990) evaluate the product-by-product constructs against four axioms: material balance, financial balance, price invariance and scale invariance. Product technology alone satisfies all four. Rueda-Cantuche and ten Raa (2009) conduct the corresponding exercise for industry-by-industry constructs and find for the fixed industry sales structure. ten Raa and Rueda-Cantuche (2003) extend the axiomatic treatment; Rueda-Cantuche and ten Raa (2013) derive econometric tests of the assumptions on establishment data.

Product technology generates negative coefficients wherever a product is made with materially different technologies in different industries, wherever classification does not align with technology, and wherever measurement error is large relative to a cell. ten Raa and Rueda-Cantuche (2013) review the proposed remedies; Almon (2000) develops a construction avoiding negatives; de Mesnard (2011) argues that inverting the supply matrix is unsound on structural grounds independent of whether negatives appear.

The relevance to learning methods is that these are not data-cleaning steps. A learned estimator produces an estimate of some object, and which object is fixed by the construct. Reporting an estimate without naming it leaves the estimand undefined.

### H.2 Valuation and units

The relation between valuations is *purchasers' prices* = *basic prices* + *trade and transport margins* + *taxes less subsidies on products*. Supply tables are published in both valuations with the bridging matrices; use tables are typically published in purchasers' prices and converted for analysis.

EEIO intensities are computed per unit of basic-price output. Corporate expenditure records are in purchasers' prices. Applying the former to the latter without conversion inflates the footprint by the margin and tax share of the expenditure, and the inflation is largest for margin-heavy categories such as retail goods. The error is systematic and one-directional, and no classification metric can see it.

On units, the material-flow literature reports magnitudes that bound what monetary inference can deliver. Revaluing imports at domestic prices is among the adjustments that change raw-material-equivalent estimates of imports and exports by tens of percent (Kovanda, Weinzettel, & Hak, 2018), and aggregating material extension categories moves national material footprints materially (de Koning et al., 2015). Hybrid supply and use tables in mass, energy and monetary units are the constructive response (Merciai & Schmidt, 2018).



### H.3 Reading reported uncertainty magnitudes

Sector-level coefficients of variation near 100% are often quoted for EXIOBASE extensions and are frequently repeated without their scope. The figure comes from one database, one year, three gases and emission accounts only, with sectoral values obtained by allocating constrained national totals under a maximum-entropy Dirichlet prior (Schulte, Jakobs, & Pauliuk, 2024). Such a prior is the widest admissible allocation consistent with the national constraint, so the resulting dispersion approximates an upper bound on allocation uncertainty in the absence of information. Read that way, it is the quantity a learned allocator is meant to reduce, and not a noise floor beneath which improvement would be undetectable. The same study documents a geographic gradient in its inputs, with national inventory uncertainties available for Annex I countries and default values used elsewhere, which is the observation §8.2 turns into a hypothesis about where circular validation would bite hardest.


---


## Appendix I. Record-level screening ledger

### I.1 Citation-database round

All 278 unique records returned by the Scopus and Web of Science searches of 4 September 2026, after removal of the 33 records shared between the two databases, with the decision taken on each. Six records duplicate studies already identified in the earlier open-index rounds and are marked as included on the same basis as before. Decisions are single-classifier judgements; the exclusion reason recorded is the first that applied, and several records would qualify under more than one.

Summary: 221 excluded at title and abstract; 15 excluded at full assessment; 42 included, of which 15 enter Appendix B.1 and 27 enter Appendix B.2. Six of the 42 duplicate studies already identified in the open-index round and are counted once in the flow of Appendix A.4. The single largest exclusion category, at 145 records, is the non-economic sense of the phrase "input-output", which is why the term set of Appendix A.2 never uses the phrase unqualified.

| # | Year | First author | Title (truncated) | Source | Decision |
|---|---|---|---|---|---|
| 1 | 2011 | Ticlavilca A.M. | Multivariate Bayesian Regression Approach to Forecast Releases from a System o… | Water Resources Management | screening: non-economic sense of "input-output" |
| 2 | 2020 | Wang B. | Prediction and comparison of the impact of COVID-19 epidemic on the financial … | Journal of Intelligent and Fuzzy S… | **included, Appendix B.2** |
| 3 | 2014 | Derkevorkian A. | Development and validation of nonlinear computational models of dispersed stru… | Earthquake Engineering and Structu… | screening: non-economic sense of "input-output" |
| 4 | 2026 | Sharma S. | AI and Big Data for Urban Sustainability: Assessing the Environmental and Econ… | Indian Journal of Environmental Pr… | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 5 | 2010 | Sreekanth J. | Multi-objective management of saltwater intrusion in coastal aquifers using ge… | Journal of Hydrology | screening: non-economic sense of "input-output" |
| 6 | 2022 | Edali M. | Pattern-oriented analysis of system dynamics models via random forests | System Dynamics Review | screening: non-economic sense of "input-output" |
| 7 | 2014 | Lee S. | Creating an advanced backpropagation neural network toolbox within GIS software | Environmental Earth Sciences | screening: non-economic sense of "input-output" |
| 8 | 2014 | Tayyebi S. | The control of MSF desalination plants based on inverse model control by neura… | Desalination | screening: non-economic sense of "input-output" |
| 9 | 2007 | Gurney K. | Neural networks for perceptual processing: From simulation tools to theories | Philosophical Transactions of the … | screening: non-economic sense of "input-output" |
| 10 | 2023 | Xu M. | Multi-task supply-demand prediction and reliability analysis for docked bike-s… | Transportation Research Part C: Em… | screening: non-economic sense of "input-output" |
| 11 | 2022 | Taccari M.L. | Attention U-Net as a surrogate model for groundwater prediction | Advances in Water Resources | screening: non-economic sense of "input-output" |
| 12 | 2011 | Wang X. | Applying support vector regression to water quality modelling by remote sensin… | International Journal of Remote Se… | screening: non-economic sense of "input-output" |
| 13 | 2011 | Lai H.-C. | Adaptive neuro-fuzzy inference system for prediction of shoreline change in Yi… | Taiwan Water Conservancy | screening: non-economic sense of "input-output" |
| 14 | 2022 | Wang Y. | Noisy Gravity Data Reconstruction Using the Convolutional Autoencoder; [利用卷积自编… | Wuhan Daxue Xuebao (Xinxi Kexue Ba… | screening: non-economic sense of "input-output" |
| 15 | 2018 | Saliminezhad A. | Validity of unbalanced growth theory and sectoral investment priorities in Ind… | Journal of International Trade and… | **included, Appendix B.2** |
| 16 | 2024 | Cherif R. | When tolstoy meets leontief: luck, policies, and learning from miracles | Structural Change and Economic Dyn… | screening: AI named but not applied |
| 17 | 2022 | Kio P.N. | Circular Economy Trends - Potential Role of Emerging Technologies | IOP Conference Series: Earth and E… | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 18 | 2014 | Roushangar K. | Modeling energy dissipation over stepped spillways using machine learning appr… | Journal of Hydrology | screening: non-economic sense of "input-output" |
| 19 | 2024 | Han G. | How Does Regional Integration Affect Carbon Emission Transfer? Evidence from t… | Resources and Environment in the Y… | **included, Appendix B.2** |
| 20 | 2019 | Fernández-Sanjurjo M. | Real-time visual detection and tracking system for traffic monitoring | Engineering Applications of Artifi… | screening: non-economic sense of "input-output" |
| 21 | 2016 | Bei X. | Learning market parameters using aggregate demand queries | 30th AAAI Conference on Artificial… | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 22 | 2026 | Escribe C. | Do sufficiency consumption changes drive emissions down? A production network … | Journal of Environmental Economics… | screening: AI named but not applied |
| 23 | 2018 | Deutsch J.M. | Computational mechanisms in genetic regulation by RNA | Journal of Theoretical Biology | screening: non-economic sense of "input-output" |
| 24 | 2026 | Hou Z. | Multistage-enhanced stochastic inverse modeling approach for efficient source … | Stochastic Environmental Research … | screening: non-economic sense of "input-output" |
| 25 | 2024 | Kim T. | Interpretable machine learning scheme for predicting bridge pier scour depth | Computers and Geotechnics | screening: non-economic sense of "input-output" |
| 26 | 2018 | Bhowmik S. | Prediction of performance and exhaust emissions of diesel engine fuelled with … | Energy and Environment | screening: non-economic sense of "input-output" |
| 27 | 2021 | Daylamani-Zad D. | Altruism and Selfishness in Believable Game Agents: Deep Reinforcement Learnin… | IEEE Transactions on Games | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 28 | 2013 | Horii H. | Estimate modelling for assessing the safety performance of occupant restraint … | WIT Transactions on the Built Envi… | screening: non-economic sense of "input-output" |
| 29 | 2012 | Ebadat A. | Well placement optimization according to field production curve using gradient… | Journal of Petroleum Science and E… | screening: non-economic sense of "input-output" |
| 30 | 2025 | Chen L. | Integration into the Industrial Chain and Enterprise Innovation: A Novel Appro… | China Finance and Economic Review | screening: AI named but not applied |
| 31 | 2025 | Hertwich E.G. | Critical Review of Climate and Resource Costs and Benefits of Machinery and Eq… | Engineering | screening: AI named but not applied |
| 32 | 2023 | Guo Y. | Domain-adapted feature transfer: A generalized framework for short-term vessel… | Ocean Engineering | screening: non-economic sense of "input-output" |
| 33 | 2026 | Liu H. | A data-driven framework for enterprise management and using system dynamics, m… | AIP Advances | **included, Appendix B.2** |
| 34 | 2026 | Ge Y. | Disparities in household carbon emissions across urban–rural and regional dime… | Energy Economics | **included, Appendix B.2** |
| 35 | 2013 | Izady A. | Application of NN-ARX Model to Predict Groundwater Levels in the Neishaboor Pl… | Water Resources Management | screening: non-economic sense of "input-output" |
| 36 | 2022 | Tu J. | SWCGAN: Generative Adversarial Network Combining Swin Transformer and CNN for … | IEEE Journal of Selected Topics in… | screening: other (proceedings summary or unrelated content) |
| 37 | 2019 | Suhartono | Deep neural network for forecasting inflow and outflow in Indonesia | Sains Malaysiana | screening: non-economic sense of "input-output" |
| 38 | 2020 | Wu D. | Research on the Measurement of Manufacturing Servitization Level in Fujian Pro… | Journal of Physics: Conference Ser… | screening: AI named but not applied |
| 39 | 2026 | Ding H. | Physics-guided phase-specific machine learning for vibration-driven droplet mi… | Computers and Geotechnics | screening: non-economic sense of "input-output" |
| 40 | 2021 | Chen A. | The economic loss prediction of flooding based on machine learning and the inp… | Atmosphere | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 41 | 2025 | Liu J. | Optimizing Communication Technology Investment for Economic Growth and Industr… | Procedia Computer Science | screening: AI named but not applied |
| 42 | 2008 | Firat M. | Hydrological time-series modelling using an adaptive neuro-fuzzy inference sys… | Hydrological Processes | screening: non-economic sense of "input-output" |
| 43 | 2008 | Ashlock D. | Characterization of extremal epidemic networks with diffusion characters | 2008 IEEE Symposium on Computation… | screening: non-economic sense of "input-output" |
| 44 | 2024 | Wang P.P. | Unveiling key drivers of economy-water system and transforming water use patte… | Journal of Cleaner Production | **included, Appendix B.2** |
| 45 | 2022 | Ding Y. | Identifying critical energy-water paths and clusters within the urban agglomer… | Energy | excluded at full assessment: singular value decomposition is classical matrix factorisation, outside the concept definition |
| 46 | 2005 | Bloom J.Z. | Market segmentation. A neural network application | Annals of Tourism Research | screening: non-economic sense of "input-output" |
| 47 | 2026 | Wang K. | Beyond connectivity: How smart 5G technologies affect carbon emissions across … | Resources, Conservation and Recycl… | screening: IO applied to the footprint of AI itself, out of scope |
| 48 | 2023 | Feng Z. | Deep Reinforcement Learning for Multi-User Massive MIMO with Channel Aging | IEEE Transactions on Machine Learn… | screening: non-economic sense of "input-output" |
| 49 | 2013 | Lujano-Rojas J.M. | Probabilistic modelling and analysis of stand-alone hybrid power systems | Energy | screening: non-economic sense of "input-output" |
| 50 | 2016 | Hassanein O. | Model-based adaptive control system for autonomous underwater vehicles | Ocean Engineering | screening: non-economic sense of "input-output" |
| 51 | 2026 | Shi Y. | Adaptive forecasting of non-equidistant industrial integration time series usi… | Advanced Engineering Informatics | screening: AI named but not applied |
| 52 | 2025 | Yang Y. | PRSA: Prompt Stealing Attacks against Real-World Prompt Services | Proceedings of the 34th USENIX Sec… | screening: non-economic sense of "input-output" |
| 53 | 2026 | Ge Z. | Evaluating the embodied carbon emissions of power infrastructure construction … | Energy Strategy Reviews | **included, Appendix B.2** |
| 54 | 2022 | Pakizeh A.H. | Application of machine-learning models to estimate regional input coefficients… | Spatial Economic Analysis | **included, Appendix B.1** |
| 55 | 2021 | Naji A. | Toward cost-effective residential energy reduction and community impacts: A da… | Energy and AI | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 56 | 2007 | Huang D.-B. | Discrete event simulation for exploring strategies: An urban water management … | Environmental Science and Technolo… | screening: non-economic sense of "input-output" |
| 57 | 2023 | Wang Y. | Global sensitivity analysis of a semi-submersible floating wind turbine using … | Ocean Engineering | screening: non-economic sense of "input-output" |
| 58 | 2023 | Yan P. | Multiscale reconstruction of porous media based on multiple dictionaries learn… | Computers and Geosciences | screening: other (proceedings summary or unrelated content) |
| 59 | 2026 | Masud F.N. | Implementing a Green ICU Pathway Across a Large U.S. Health System: An Observa… | Critical Care Explorations | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 60 | 2012 | Duan W. | Input output table updating based on Agent-Responses Equilibrium model | 2012 IEEE Conference on Computatio… | screening: AI named but not applied |
| 61 | 2024 | Benzaamia A. | Predicting the shear strength of rectangular RC beams strengthened with extern… | Engineering Structures | screening: non-economic sense of "input-output" |
| 62 | 2024 | Zhang S. | TrafficGPT: Viewing, processing and interacting with traffic foundation models | Transport Policy | screening: non-economic sense of "input-output" |
| 63 | 2023 | Ma Z. | A BPNN-based ecologically extended input–output model for virtual water metabo… | Environmental Science and Pollutio… | **included, Appendix B.2** |
| 64 | 2026 | ZOU Y. | Research on carbon footprint and embodied carbon transfer prediction of advanc… | Journal of Environmental Engineeri… | excluded at full assessment: redundant report of an included study |
| 65 | 2022 | Florez-Perez L. | Using machine learning to analyze and predict construction task productivity | Computer-Aided Civil and Infrastru… | screening: non-economic sense of "input-output" |
| 66 | 2025 | Zeng J. | Research on the evaluation method system for recycling and utilization of spen… | Journal of Energy Storage | screening: AI named but not applied |
| 67 | 2023 | Chen N. | Intelligent Identification and Verification of Flutter Derivatives and Critica… | Atmosphere | screening: non-economic sense of "input-output" |
| 68 | 2026 | Zhao L. | Global maritime embedded carbon flow network: Key factors and formation mechan… | Transportation Research Part E: Lo… | **included, Appendix B.2** |
| 69 | 2022 | Liu M. | Construction of Resource Element Portrait Analysis Model Based on Data Center | Proceedings - 2022 2nd Internation… | screening: non-economic sense of "input-output" |
| 70 | 2015 |  | International Conference on Applied Engineering Sciences, ICAES 2014 | Applied Engineering Sciences - Pro… | screening: other (proceedings summary or unrelated content) |
| 71 | 2020 | Coskun H. | Static ecological system measures: A holistic analysis of compartmental systems | Theoretical Ecology | screening: non-economic sense of "input-output" |
| 72 | 2022 | Elhorst P. | Raising the bar (20) | Spatial Economic Analysis | screening: other (proceedings summary or unrelated content) |
| 73 | 2025 | Chen X. | How is artificial intelligence shaping the labor demand of firms? -evidence f… | Telecommunications Policy | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 74 | 2025 | Präger L. | LCA-based calculation of GHG Protocol Scope 3: A bottom-up approach to determi… | Building and Environment | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 75 | 2022 | Verma R. | ANN-based Rainfall-Runoff Model and Its Performance Evaluation of Sabarmati Ri… | Water Conservation Science and Eng… | screening: non-economic sense of "input-output" |
| 76 | 2025 | Qin Z. | Hierarchical speed control of an infinitely variable transmission in tidal cur… | Ocean Engineering | screening: non-economic sense of "input-output" |
| 77 | 2025 | Hu Q. | Impacts of IOD and ENSO on the phytoplankton’s vertical variability in the Nor… | Frontiers in Marine Science | screening: other (proceedings summary or unrelated content) |
| 78 | 2010 | Martí P. | Integrated emitter local loss prediction using artificial neural networks | Journal of Irrigation and Drainage… | screening: non-economic sense of "input-output" |
| 79 | 2013 | Ticlavilca A.M. | Real-time forecasting of short-term irrigation canal demands using a robust mu… | Irrigation Science | screening: non-economic sense of "input-output" |
| 80 | 2010 | Styczen M. | Management model for decision support when applying low quality water in irrig… | Agricultural Water Management | screening: non-economic sense of "input-output" |
| 81 | 2025 | Hou C. | Multi-Dimensional Safety Assessments of LLM-Assisted Driving Systems | IECON Proceedings (Industrial Elec… | screening: non-economic sense of "input-output" |
| 82 | 2025 | Zheng Y. | Structure optimization of landscape functional spaces based on land input-bene… | Chinese Journal of Applied Ecology | screening: non-economic sense of "input-output" |
| 83 | 2022 | Liu G. | Data-driven seismic prestack velocity inversion via combining residual network… | Journal of Applied Geophysics | screening: non-economic sense of "input-output" |
| 84 | 2025 | Fukui S. | Estimating Input Coefficients for Regional Input–Output Tables Using Deep Lear… | Computational Economics | **included, Appendix B.1** |
| 85 | 2020 | Mohanty S. | Region-wide congestion prediction and control using deep learning | Transportation Research Part C: Em… | screening: non-economic sense of "input-output" |
| 86 | 2026 | Wang S. | Dynamic pricing and electricity sales strategy for charging operators consider… | IET Conference Proceedings | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 87 | 2020 |  | Construction Research Congress 2020: Computer Applications - Selected Papers f… | Construction Research Congress 202… | screening: other (proceedings summary or unrelated content) |
| 88 | 2013 | Sefeedpari P. | Application of artificial neural network to model the energy output of dairy f… | International Journal of Energy Te… | screening: non-economic sense of "input-output" |
| 89 | 2000 | Ito Y. | Adaptive dynamic input-output analysis using neural networks Japanese industri… | Kybernetes | **included, Appendix B.2** |
| 90 | 2026 | Zou Y. | Reconstruction and Forecasting of Carbon Footprints and Embodied Transfers in … | Networks and Spatial Economics | **included, Appendix B.2** |
| 91 | 2026 | Zhao L. | The impact of inter-country differences on transportation carbon emission tran… | Transport Policy | **included, Appendix B.2** |
| 92 | 2003 | Saraph P. | Test case generation and reduction by automated input-output analysis | Proceedings of the IEEE Internatio… | screening: non-economic sense of "input-output" |
| 93 | 2024 | Wang Z. | A factorial-analysis-based Bayesian neural network method for quantifying Chin… | Science of the Total Environment | screening: non-economic sense of "input-output" |
| 94 | 2018 | Yilma M. | Application of artificial neural network in water quality index prediction: a … | Modeling Earth Systems and Environ… | screening: non-economic sense of "input-output" |
| 95 | 2011 | Zhang Y. | Notice of Retraction: Effect of offshore outsourcing on the productivity growt… | 2011 2nd International Conference … | screening: AI named but not applied |
| 96 | 2026 | Yao Y. | GenAI investment in the industrial chain and firm breakthrough innovation | Finance Research Letters | screening: AI named but not applied |
| 97 | 2022 | Sofianos E. | Mind the gap: forecasting euro-area output gaps with machine learning | Applied Economics Letters | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 98 | 2010 | Yu T. | Large-scale computational modeling for environmental impact assessment | Environmental Modeling for Sustain… | excluded at full assessment: learned component unspecified within a constrained estimation system |
| 99 | 2025 | Maddah S. | Improving deep learning-based flood susceptibility modeling by integrating dat… | Natural Hazards | screening: non-economic sense of "input-output" |
| 100 | 2024 | Li W. | Research on the Influence of Inter-Industry Cascade Relationships Based on Rei… | ACM International Conference Proce… | **included, Appendix B.2** |
| 101 | 2023 | Zhong S.H. | A machine learning method for distinguishing detrital zircon provenance | Contributions to Mineralogy and Pe… | screening: non-economic sense of "input-output" |
| 102 | 2020 | De Pablo Valenciano J. | Triangulation Applied to the Intra-European Union Tomato Market | Complexity | screening: AI named but not applied |
| 103 | 2026 | Faridzad A. | Financial Sector Linkages and Real Economy Impacts in Malaysia: Evidence from … | Asian Development Review | **included, Appendix B.2** |
| 104 | 2026 | Okafor K.C. | Compartmental Modeling of Woodland Ecosystem Services for Evaluating Urban Nat… | Engineering Reports | screening: AI named but not applied |
| 105 | 2018 | Ohsato T. | Developing an input-output table generation algorithm using a Japanese trade d… | Lecture Notes in Computer Science … | excluded at full assessment: text mining plus a deterministic generation algorithm, no learned model |
| 106 | 2019 | Chen G. | Urban-rural disparities of household energy requirements and influence factors… | Applied Energy | **included, Appendix B.2** |
| 107 | 2015 | Papale D. | Effect of spatial sampling from European flux towers for estimating carbon and… | Journal of Geophysical Research: B… | screening: non-economic sense of "input-output" |
| 108 | 2007 | Maruyama T. | Regional reference total electron content model over Japan based on neural net… | Annales Geophysicae | screening: non-economic sense of "input-output" |
| 109 | 2023 | Zhou B. | An input-output-based Bayesian neural network method for analyzing carbon redu… | Journal of Cleaner Production | **included, Appendix B.2** |
| 110 | 2024 | Yang X. | Random Mask Perturbation Based Explainable Method of Graph Neural Networks | Lecture Notes in Computer Science | screening: non-economic sense of "input-output" |
| 111 | 2025 | Ma Y. | A synergistic optimization framework for implicit stochastic operations of a m… | Journal of Hydrology | screening: non-economic sense of "input-output" |
| 112 | 2023 | Zhu Z. | A Bayesian clustering ensemble Gaussian process model for network-wide traffic… | Transportation Research Part C: Em… | screening: non-economic sense of "input-output" |
| 113 | 2018 | Udias A. | A decision support tool to enhance agricultural growth in the Mékrou river bas… | Computers and Electronics in Agric… | screening: non-economic sense of "input-output" |
| 114 | 2026 | Le H.N. | The More, the Merrier? Innovation-Led Sustainable Development | Sustainable Development | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 115 | 2026 | Li S. | An Input–output Analysis CNN-LSTM Model for Analyzing the Virtual Water Consum… | Environmental Science and Engineer… | **included, Appendix B.2** |
| 116 | 2026 | Zadmirzaei M. | Data envelopment analysis in forestry over three decades: an in-depth review o… | Environment, Development and Susta… | screening: non-economic sense of "input-output" |
| 117 | 2022 | Sirin S.M. | How do variable renewable energy technologies affect firm-level day-ahead outp… | Energy Economics | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 118 | 2025 | Arellano C.J. | A Comparative Evaluation of Target Datasets for U-Net-Based Precipitation Esti… | Journal of Hydrometeorology | screening: non-economic sense of "input-output" |
| 119 | 2026 | Tan Y. | Multi-Source Enterprise Data for Fine-Grained Industrial Cluster Delineation: … | Applied Spatial Analysis and Policy | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 120 | 2026 | Zheng C. | Input-output sensitivity analysis model construction and multi-objective weigh… | Proceedings of SPIE - The Internat… | **included, Appendix B.1** |
| 121 | 2018 | Honorato A.G.D.S.M. | Monthly streamflow forecasting using neuro-wavelet techniques and input analys… | Hydrological Sciences Journal | screening: non-economic sense of "input-output" |
| 122 | 2025 | Hou X. | A multi-regional input-output database linking Chinese subnational regions and… | Scientific Data  | **included, Appendix B.1** |
| 123 | 2009 | Wu X. | Computer analysis algorithm for stability of the extended dynamic leontief inp… | Proceedings of the 2009 Internatio… | screening: AI named but not applied |
| 124 | 2022 | Şalap-Ayça S. | Self-organizing maps as a dimension reduction approach for spatial global sens… | Transactions in GIS | screening: non-economic sense of "input-output" |
| 125 | 2019 | Chain C.P. | BIBLIOMETRIC ANALYSIS OF THE QUANTITATIVE METHODS APPLIED TO THE MEASUREMENT O… | Journal of Economic Surveys | screening: AI named but not applied |
| 126 | 2011 | Su H. | Study on an Intelligent Inference Engine in Early-Warning System of Dam Health | Water Resources Management | screening: non-economic sense of "input-output" |
| 127 | 2014 | Li D.-C. | Employing box plots to build high-dimensional manufacturing models for new pro… | Neurocomputing | screening: non-economic sense of "input-output" |
| 128 | 2025 | Parraga E. | A Methodical Approach to Parallel IO Analysis in Distributed Deep Learning App… | Communications in Computer and Inf… | screening: non-economic sense of "input-output" |
| 129 | 2023 | Fang C. | A Detailed Examination of China’s Clean Energy Mineral Consumption: Footprints… | Sustainability (Switzerland) | **included, Appendix B.2** |
| 130 | 2011 | Tatari O. | Cost premium prediction of certified green buildings: A neural network approach | Building and Environment | screening: non-economic sense of "input-output" |
| 131 | 2025 | Aparicio J. | An innovative approach to efficiency measurement: Combining convexified effici… | Socio-Economic Planning Sciences | screening: non-economic sense of "input-output" |
| 132 | 2022 | Petetin H. | Model output statistics (MOS) applied to Copernicus Atmospheric Monitoring Ser… | Atmospheric Chemistry and Physics | screening: non-economic sense of "input-output" |
| 133 | 2020 | Yan C. | Auto-Suggest: Learning-to-Recommend Data Preparation Steps Using Data Science … | Proceedings of the ACM SIGMOD Inte… | screening: non-economic sense of "input-output" |
| 134 | 2025 | Li Y. | Analysis of low carbon transformation strategy and CO2 emission metabolism in … | Journal of Industrial Ecology | screening: AI named but not applied |
| 135 | 2021 | Pan Z. | Simultaneous identification of groundwater pollution source spatial–temporal c… | Journal of Hydrology | screening: non-economic sense of "input-output" |
| 136 | 2023 | Zhang S. | DeepQRE: A QRE System Based on Deep Learning | 2023 9th International Conference … | screening: non-economic sense of "input-output" |
| 137 | 2016 | Yu T. | Computational Intelligent Data Analysis for Sustainable Development | Computational Intelligent Data Ana… | screening: AI named but not applied |
| 138 | 2015 | Amritha S. | Traffic density estimation using dimensional analysis | IEEE Intelligent Vehicles Symposiu… | screening: non-economic sense of "input-output" |
| 139 | 2021 | Narayana S. | Fair and Efficient Allocations with Limited Demands | 35th AAAI Conference on Artificial… | screening: AI named but not applied |
| 140 | 2023 | Zhi J. | Multi-scale near-long-range flow measurement and analysis of virtual water in … | Process Safety and Environmental P… | **included, Appendix B.2** |
| 141 | 2026 | Lu X. | A novel automated policy text evaluation framework integrating PMC into large … | Information Processing and Managem… | screening: non-economic sense of "input-output" |
| 142 | 2023 | Qu P.-F. | Meta-modeling of fractional constitutive relationships for rocks based on phys… | International Journal for Numerica… | screening: non-economic sense of "input-output" |
| 143 | 2001 | Wang S. | The neural network approach to input-output analysis for economic systems | Neural Computing and Applications | **included, Appendix B.1** |
| 144 | 2016 | Liu X. | A grey neural network and input-output combined forecasting model. Primary ene… | Energy | **included, Appendix B.2** |
| 145 | 2011 | Jabbari E. | Using Artificial Neural Networks for estimation of scour at the head of vertic… | Journal of Coastal Research | screening: non-economic sense of "input-output" |
| 146 | 2026 | Wang L. | An integrated method to account for river flood mitigation service in the SEEA… | Ecosystem Services | **included, Appendix B.1** |
| 147 | 2008 | Budha M. | Generation of PLC ladder diagram using modular structure | 2008 International Conference on C… | screening: non-economic sense of "input-output" |
| 148 | 2020 | Tsionas M.G. | On a High-Dimensional Model Representation method based on Copulas | European Journal of Operational Re… | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 149 | 2020 | De Clercq D. | Interpretable machine learning for predicting biomethane production in industr… | Science of the Total Environment | screening: non-economic sense of "input-output" |
| 150 | 2011 | Zhang B. | Changes of industrial linkage degree in EMI and determination of the stage of … | 2011 2nd International Conference … | screening: AI named but not applied |
| 151 | 2004 | Last M. | Using data mining for automated software testing | International Journal of Software … | screening: non-economic sense of "input-output" |
| 152 | 2025 | Kumar P. | Experimental study of the in-cylinder pressure and performance of a biogas fue… | Energy | screening: non-economic sense of "input-output" |
| 153 | 2022 | Wild A. | Multi-donor Neural Transfer Learning for Genetic Programming | ACM Transactions on Evolutionary L… | screening: non-economic sense of "input-output" |
| 154 | 2006 | Wu Y. | Recurrent neural network control of functional electrical stimulation systems | ICBPE 2006 - Proceedings of the 20… | screening: non-economic sense of "input-output" |
| 155 | 2025 | Karbevska L. | Mapping global value chains at the product level | EPJ Data Science | excluded at full assessment: proportional allocation rule; machine-learning framing only |
| 156 | 2025 | Senol E. | Brain-wide input-output analysis of tuberal nucleus somatostatin neurons revea… | Nature Communications  | screening: non-economic sense of "input-output" |
| 157 | 2023 | He X. | Ready-to-use deep-learning surrogate models for problems with spatially variab… | Acta Geotechnica | screening: non-economic sense of "input-output" |
| 158 | 2021 | Latif S.D. | Evaluation of deep learning algorithm for inflow forecasting: a case study of … | Natural Hazards | screening: non-economic sense of "input-output" |
| 159 | 2026 | Li S.Z. | Coupling input-output analysis with deep learning to quantify the carrying cap… | Journal of Cleaner Production | **included, Appendix B.2** |
| 160 | 2021 | Samothrakis S. | Artificial Intelligence inspired methods for the allocation of common goods an… | PLoS ONE | screening: AI named but not applied |
| 161 | 2026 | Iranmehr S. | Improving short-term water demand forecasting with development of dynamic neur… | International Journal of Environme… | screening: non-economic sense of "input-output" |
| 162 | 2025 | Parraga E. | Parallel I/O analysis in distributed deep learning applications on high-perfor… | Journal of Supercomputing | screening: non-economic sense of "input-output" |
| 163 | 2022 | Zhao B. | Using Deep Learning to Fill Data Gaps in Environmental Footprint Accounting | Environmental Science and Technolo… | **included, Appendix B.1** |
| 164 | 2007 | Ozkaya B. | Neural network prediction model for the methane fraction in biogas from field-… | Environmental Modelling and Softwa… | screening: non-economic sense of "input-output" |
| 165 | 2014 | Kialashaki A. | Development and validation of artificial neural network models of the energy d… | Energy | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 166 | 2024 | Tao M. | Enhancing New Zealand's emissions trading scheme: A comprehensive sector-level… | Journal of Environmental Management | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 167 | 2015 | Court C.D. | Can hazardous waste supply chain 'hotspots' be identified using an input-outpu… | European Journal of Operational Re… | screening: AI named but not applied |
| 168 | 2009 | Pintea C.-M. | A hybrid ant-based approach to the economic triangulation problem for input-ou… | Lecture Notes in Computer Science … | screening: AI named but not applied |
| 169 | 2022 | Chen K. | Recent advances in carbon footprint studies of urban ecosystems: overview, app… | Environmental Reviews | screening: AI named but not applied |
| 170 | 2020 | Bolandnazar E. | Energy consumption forecasting in agriculture by artificial intelligence and m… | Energy Sources, Part A: Recovery, … | screening: non-economic sense of "input-output" |
| 171 | 2022 | Rago F. | A New Matrix Model for Human-AI Integration | Lecture Notes in Networks and Syst… | screening: AI named but not applied |
| 172 | 2026 | Guo Y. | Global emission factor dataset for Scope 3 machine learning applications | Scientific Data  | **included, Appendix B.1** |
| 173 | 2026 | Li Y. | Industrial robot adoption and the resilience of manufacturing global value cha… | Structural Change and Economic Dyn… | screening: AI named but not applied |
| 174 | 2022 | Clemett N. | Optimal seismic retrofitting of existing buildings considering environmental i… | Engineering Structures | screening: AI named but not applied |
| 175 | 2027 | Tang Y. | What climate policies facilitate sectoral mitigation? Global evidence from thr… | Environmental Impact Assessment Re… | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 176 | 2020 | Zhang R. | Physics-guided convolutional neural network (PhyCNN) for data-driven seismic r… | Engineering Structures | screening: non-economic sense of "input-output" |
| 177 | 2023 | Zhao Y. | Estimation of the barrier layer thickness in the Indian Ocean based on hybrid … | Deep-Sea Research Part I: Oceanogr… | screening: non-economic sense of "input-output" |
| 178 | 2025 | Davidescu A.A. | A Machine Learning and Econometric Framework for Credibility-Aware AI Adoption… | Mathematics | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 179 | 2024 | Chen D. | Has Artificial Intelligence Promoted Manufacturing Servitization: Evidence fro… | Sustainability (Switzerland)  | screening: AI named but not applied |
| 180 | 2012 | Resurreccion J. | Multiobjective Prioritization Methodology and Decision Support System for Eval… | Risk Analysis | screening: AI named but not applied |
| 181 | 2025 | Al-Kuwari A. | Life cycle sustainability assessment of electricity production technologies: a… | Energy Strategy Reviews | screening: AI named but not applied |
| 182 | 2020 | Farzanfar A. | Physiological constraints of visual pathway lead to more efficient coding of i… | Journal of Theoretical Biology | screening: non-economic sense of "input-output" |
| 183 | 1990 | Tseng P. | Partially asynchronous, parallel algorithms for network flow and other problems | SIAM Journal on Control and Optimi… | screening: AI named but not applied |
| 184 | 2026 | Chen Z. | The potential impact of artificial intelligence on CO2 emissions: A comparison… | Technology in Society | screening: AI named but not applied |
| 185 | 2018 | Araghinejad S. | Development of a Hybrid Data Driven Model for Hydrological Estimation | Water Resources Management | screening: non-economic sense of "input-output" |
| 186 | 2026 | De Pretis F. | Keeping up with the regions: a hybrid machine learning framework for estimatin… | Scientific Reports | **included, Appendix B.1** |
| 187 | 2010 | Huang Y. | Multiobjective water quality model calibration using a hybrid genetic algorith… | Journal of Environmental Engineeri… | screening: non-economic sense of "input-output" |
| 188 | 2024 | Tang Y. | Multi-output prediction for TBM operation parameters based on stacking ensembl… | Tunnelling and Underground Space T… | screening: non-economic sense of "input-output" |
| 189 | 2011 | Liang B. | Association analyses on logistics industry of Henan province with input-output… | 2011 2nd International Conference … | screening: AI named but not applied |
| 190 | 2026 | Tripathi B.K. | Prediction of gas production for shale matrix–fracture systems using deep oper… | Energy Geoscience | screening: non-economic sense of "input-output" |
| 191 | 2018 |  | 9th JSAI International Symposium on Artificial Intelligence, JSAI-isAI 2017 | Lecture Notes in Computer Science … | screening: other (proceedings summary or unrelated content) |
| 192 | 2024 | Katsanevakis S. | GuardIAS – Guarding European Waters from Invasive Alien Species | Management of Biological Invasions | screening: AI named but not applied |
| 193 | 2024 | Li M. | A high-resolution multi-scale industrial water use dataset in China | Scientific Data  | screening: AI named but not applied |
| 194 | 2015 | McDonald S. | Modelling retinal ganglion cells using self-organising fuzzy neural networks | Proceedings of the International J… | screening: non-economic sense of "input-output" |
| 195 | 2022 | Guo D. | Optimization of fracturing parameters for tight oil production based on geneti… | Petroleum | screening: non-economic sense of "input-output" |
| 196 | 2017 | Lippmann K. | Epileptiform activity and spreading depolarization in the blood-brain barrier-… | Journal of Cerebral Blood Flow and… | screening: non-economic sense of "input-output" |
| 197 | 2020 | Xu X. | Projecting China's future water footprint under the shared socio-economic path… | Journal of Environmental Management | screening: AI named but not applied |
| 198 | 2007 | Borst A. | Correlation versus gradient type motion detectors: The pros and cons | Philosophical Transactions of the … | screening: non-economic sense of "input-output" |
| 199 | 2019 | Huang A. | Input-Output Analysis of Chinese National Agricultural Science and Technology … | Lecture Notes in Computer Science … | screening: non-economic sense of "input-output" |
| 200 | 2017 |  | AIP Conference Proceedings | AIP Conference Proceedings | screening: AI named but not applied |
| 201 | 2019 | Mitrović T. | Virtual water quality monitoring at inactive monitoring sites using Monte Carl… | Science of the Total Environment | screening: non-economic sense of "input-output" |
| 202 | 2022 | Bajirao T.S. | Applicability of machine learning techniques for multi-time step ahead runoff … | Acta Geophysica | screening: non-economic sense of "input-output" |
| 203 | 2025 | Jiang M. | Global value chain restructuring driven by critical material trade: a case stu… | Resources, Conservation and Recycl… | screening: AI named but not applied |
| 204 | 2025 | Zou Y. | Spatiotemporal Evolution and Drivers of the Carbon Footprint and Embodied Carb… | Sustainability (Switzerland) | excluded at full assessment: redundant report of an included study |
| 205 | 2025 | Parraga E. | An Empirical Method for Processing I/O Traces to Analyze the Performance of DL… | Communications in Computer and Inf… | screening: non-economic sense of "input-output" |
| 206 | 2021 | Yin S. | Dominant Resource Fairness with Meta-Types | IJCAI International Joint Conferen… | screening: AI named but not applied |
| 207 | 2015 | Li W.-H. | Modeling welding deviation of rotating arc NGW based on support vector machine | Advances in Intelligent Systems an… | screening: non-economic sense of "input-output" |
| 208 | 2025 | Das A. | Estimation of barrier layer thickness from satellite-derived sea surface param… | International Journal of Remote Se… | screening: non-economic sense of "input-output" |
| 209 | 2024 | Sedghnejad N. | Comparative analysis of classification techniques and input-output patterns fo… | Water Science | screening: non-economic sense of "input-output" |
| 210 | 2023 | Huang L. | A Multi Objective and Dynamic Input Output Optimization Model and Algorithm | Procedia Computer Science | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 211 | 2015 | Porkhial S. | Modeling and prediction of geothermal reservoir temperature behavior using evo… | Geothermics | screening: non-economic sense of "input-output" |
| 212 | 2024 | Pang L. | Can digital economy enhance the control of key links in the industrial chain? … | Studies in Science of Science | screening: AI named but not applied |
| 213 | 2026 | Kim H. | Construction supply-chain carbon footprint with graph neural network-based inp… | Building and Environment | **included, Appendix B.1** |
| 214 | 2023 | Braendle U.C. | Digital Risk in International Business Management and Allied Areas in India, t… | Internet of Things | screening: non-economic sense of "input-output" |
| 215 | 2020 | Dtissibe F.Y. | Flood forecasting based on an artificial neural network scheme | Natural Hazards | screening: non-economic sense of "input-output" |
| 216 | 2026 | Amine B.M. | Resolution of linear interval systems using neural networks and their applicat… | Statistics, Optimization and Infor… | **included, Appendix B.1** |
| 217 | 2026 | Huang Y.-H. | The Economic and Environmental Impacts of Floating Offshore Wind Power Generat… | Sustainability (Switzerland) | screening: AI named but not applied |
| 218 | 2021 | Elhag M. | Input/output inconsistencies of daily evapotranspiration conducted empirically… | Open Geosciences | screening: non-economic sense of "input-output" |
| 219 | 2026 | Fazal R. | Estimating concordance matrices using Artificial Intelligence | Economic Systems Research | **included, Appendix B.1** |
| 220 | 2012 | Pahlavan R. | Energy input-output analysis and application of artificial neural networks for… | Energy | screening: non-economic sense of "input-output" |
| 221 | 1992 | Shi B.E. | Resistive Grid Image Filtering: Input/Output Analysis via the CNN Framework | IEEE Transactions on Circuits and … | screening: non-economic sense of "input-output" |
| 222 | 2026 | Costa C.J. | Socio-Economic Consequences of Generative AI: A Review of Methodological Appro… | Lecture Notes in Networks and Syst… | screening: AI named but not applied |
| 223 | 2025 | Hazari B. | A Note on the Implications of Automation and Artificial Intelligence for Inter… | Arthaniti: Journal of Economic The… | screening: AI named but not applied |
| 224 | 2025 | Luo Q. | The impact of artificial intelligence development on embodied carbon emissions… | Energy Policy | screening: AI named but not applied |
| 225 | 2010 | Özçelik R. | Estimating tree bole volume using artificial neural network models for four sp… | Journal of Environmental Management | screening: non-economic sense of "input-output" |
| 226 | 2019 | Coskun H. | Nonlinear decomposition principle and fundamental matrix solutions for dynamic… | Discrete and Continuous Dynamical … | screening: AI named but not applied |
| 227 | 2024 | Ye X.-W. | Confining pressure forecasting of shield tunnel lining during construction bas… | Tunnelling and Underground Space T… | screening: non-economic sense of "input-output" |
| 228 | 2020 | Abdella G.M. | Sustainability assessment and modeling based on supervised machine learning te… | Journal of Cleaner Production | **included, Appendix B.2** |
| 229 | 2020 | Zhang L. | Input-output Analysis of Agricultural Economic Benefits Based on Big Data and … | Journal of Physics: Conference Ser… | screening: AI named but not applied |
| 230 | 2023 | Zhang S. | SQL Synthesis with Input-Output Example Based on Deep Learning | Proceedings of the International J… | screening: non-economic sense of "input-output" |
| 231 | 2021 | Mirmozaffari M. | A novel artificial intelligent approach: comparison of machine learning tools … | International Journal of Energy Se… | screening: non-economic sense of "input-output" |
| 232 | 2019 | Fernández-Sanjurjo M. | Real-Time Traffic Monitoring with Occlusion Handling | Lecture Notes in Computer Science … | screening: non-economic sense of "input-output" |
| 233 | 2013 | Torabi S.R. | Study of the influence of geotechnical parameters on the TBM performance in Te… | Arabian Journal of Geosciences | screening: non-economic sense of "input-output" |
| 234 | 2007 | Parasuraman K. | Cluster-based hydrologic prediction using genetic algorithm-trained neural net… | Journal of Hydrologic Engineering | screening: non-economic sense of "input-output" |
| 235 | 2023 | Faghfouri A. | A novel statistical model for flood prediction in the Eel River watershed, New… | Water Science | screening: non-economic sense of "input-output" |
| 236 | 2024 | Ali W. | A novel application of neural time series for dynamic characteristic analysis … | Ocean Engineering | screening: non-economic sense of "input-output" |
| 237 | 2026 | Jo J.-H. | An Economic Impact Analysis of Transmission and Substation Network Investments… | Land | screening: AI named but not applied |
| 238 | 2024 | Khankhoje T. | River system sediment flow modeling using artificial neural networks | International Journal of Sediment … | screening: non-economic sense of "input-output" |
| 239 | 2022 | Pang Z. | Prediction of Household Carbon Emissions Based on SP-LIME and Ensemble Learnin… | 2022 IEEE 5th International Confer… | **included, Appendix B.2** |
| 240 | 2026 | Zhang Z. | Unveiling Scope 3 emissions in energy supply chains: a graph neural network ap… | Frontiers in Energy Research | **included, Appendix B.1** |
| 241 | 2024 | Peters B. | Fully invertible hyperbolic neural networks for segmenting large-scale surface… | Artificial Intelligence in Geoscie… | screening: non-economic sense of "input-output" |
| 242 | 2025 | Niu F. | Origins, compilation methods, and development trends of input-output tables | Progress in Geography | screening: AI named but not applied |
| 243 | 2013 | Özçelik R. | Estimating Crimean juniper tree height using nonlinear regression and artifici… | Forest Ecology and Management | screening: non-economic sense of "input-output" |
| 244 | 2025 | Faridzad A. | Applying machine learning to input–output analysis: a new perspective on ident… | Journal of Economic Structures | **included, Appendix B.2** |
| 245 | 2021 | Taymouri F. | Business process variant analysis: Survey and classification | Knowledge-Based Systems | screening: non-economic sense of "input-output" |
| 246 | 2025 | Li M. | Redefining limits: Toward planetary boundaries – informed absolute environment… | Encyclopedia of Agriculture and Fo… | screening: AI named but not applied |
| 247 | 2023 | Liu D. | Analysis of Carbon Emissions Embodied in the Provincial Trade of China Based o… | Sustainability (Switzerland) | **included, Appendix B.2** |
| 248 | 2002 | Papadas C.T. | Neural network forecasts of input-output technology | Applied Economics | **included, Appendix B.1** |
| 249 | 2025 |  | 15th International Conference on Environmental Science and Technology, ICEST 2… | Environmental Science and Engineer… | screening: AI named but not applied |
| 250 | 2025 | Liu D. | Regional Differences Reflected in Resource Flow in China: Multidimensional Ana… | ACS Sustainable Chemistry and Engi… | **included, Appendix B.2** |
| 251 | 2025 | Di Santo D. | ML-AMPSIT: Machine Learning-based Automated Multi-method Parameter Sensitivity… | Geoscientific Model Development | screening: non-economic sense of "input-output" |
| 252 | 2014 | Obagbuwa I.C. | A modified roach infestation optimization | 2014 IEEE Conference on Computatio… | screening: other (proceedings summary or unrelated content) |
| 253 | 2025 | Leon B. | Analyzing the Influence of File Formats on I/O Patterns in Deep Learning | Communications in Computer and Inf… | screening: non-economic sense of "input-output" |
| 254 | 2025 | Yiou P. | Using artificial intelligence to identify CMIP6 models from daily SLP maps | npj Climate and Atmospheric Science | screening: non-economic sense of "input-output" |
| 255 | 2025 | Shi Q. | Tar yield prediction of tar-rich coal based on geophysical logging data: Compa… | Computers and Geosciences | screening: non-economic sense of "input-output" |
| 256 | 2018 | Dezfooli D. | Classification of water quality status based on minimum quality parameters: ap… | Modeling Earth Systems and Environ… | screening: non-economic sense of "input-output" |
| 257 | 2008 | Scozzari A. | Non-invasive methods applied to the case of Municipal Solid Waste landfills (M… | Advances in Geosciences | screening: non-economic sense of "input-output" |
| 258 | 2022 | Ma W. | Research on the impact of artificial intelligence on international specializat… | Journal of Silk | screening: AI named but not applied |
| 259 | 2025 | Chu X. | Strategic Model for Digital Economic Transformation of Rural Industries Based … | Journal of Quality | excluded at full assessment: learning separated from the IO object by an intervening deterministic model, or acting on a non-IO quantity |
| 260 | 2024 | Li W. | Impact of CBAM on carbon emission reduction in global steel foreign trade: pro… | Energy Sources, Part B: Economics,… | **included, Appendix B.2** |
| 261 | 2024 | Wang W. | Exploring the relationship between digital transformation of enterprises and “… | Applied Mathematics and Nonlinear … | screening: AI named but not applied |
| 262 | 2015 | McDonald | Modelling Retinal Ganglion Cells using Self-Organising Fuzzy Neural Networks | 2015 INTERNATIONAL JOINT CONFERENC… | screening: non-economic sense of "input-output" |
| 263 | 2006 | Yilei | Recurrent neural network control of functional electrical stimulation systems | 2006 INTERNATIONAL CONFERENCE ON B… | screening: non-economic sense of "input-output" |
| 264 | 2023 | Tranos | Using the Web to Predict Regional Trade Flows: Data Extraction, Modeling, and … | ANNALS OF THE AMERICAN ASSOCIATION… | **included, Appendix B.1** |
| 265 | 2012 | Safa | Modelling Energy Use and Fuel Consumption in Wheat Production Using Indirect F… | NEURAL INFORMATION PROCESSING, ICO… | screening: non-economic sense of "input-output" |
| 266 | 2019 | Nikkhah | Integration of principal component analysis and artificial neural networks to … | ENVIRONMENTAL PROGRESS & SUSTAINAB… | screening: non-economic sense of "input-output" |
| 267 | 2020 | Cheng | Using a temporal input-output approach to analyze the ripple effect of China's… | ENERGY | screening: AI named but not applied |
| 268 | 2022 | Belouz | Prediction of greenhouse tomato yield using artificial neural networks combine… | SCIENTIA HORTICULTURAE | screening: non-economic sense of "input-output" |
| 269 | 2023 | Kaur | Artificial Neural Network Model to Forecast Energy Consumption in Wheat Produc… | JOURNAL OF STATISTICAL THEORY AND … | screening: non-economic sense of "input-output" |
| 270 | 2016 | Kalhor | Modeling of energy ratio index in broiler production units using artificial ne… | SUSTAINABLE ENERGY TECHNOLOGIES AN… | screening: non-economic sense of "input-output" |
| 271 | 2011 | Safa | Determination and modelling of energy consumption in wheat production using ne… | ENERGY | screening: non-economic sense of "input-output" |
| 272 | 2023 | Khalaj | Use of life cycle assessment and modeling techniques for prediction of energy-… | ENVIRONMENTAL AND SUSTAINABILITY I… | screening: non-economic sense of "input-output" |
| 273 | 2019 | Yu | Factor decomposition of China's industrial electricity consumption using struc… | STRUCTURAL CHANGE AND ECONOMIC DYN… | screening: AI named but not applied |
| 274 | 2026 | Yang | Carbon footprint analysis and its underlying drivers in a mega-urban region: E… | JOURNAL OF CLEANER PRODUCTION | screening: AI named but not applied |
| 275 | 2023 | Sharafi | Estimating energy consumption and GHG emissions in crop production: A machine … | JOURNAL OF CLEANER PRODUCTION | screening: non-economic sense of "input-output" |
| 276 | 2015 | Hamedani | Comparative Study of Soft Computing Methodologies for Energy Input-Output Anal… | AMERICAN JOURNAL OF POTATO RESEARCH | screening: non-economic sense of "input-output" |
| 277 | 2018 | Vance | Bioinspired Approach to Modeling Retinal Ganglion Cells Using System Identific… | IEEE TRANSACTIONS ON NEURAL NETWOR… | screening: non-economic sense of "input-output" |
| 278 | 2022 | Xiang | Research on the economic and environmental impacts of China's seawater desalin… | DESALINATION | screening: AI named but not applied |


## Appendix I.2 OpenAlex round

All 101 records returned by the OpenAlex search of 4 September 2026 that were new after de-duplication against the citation-database and open-index rounds. Summary: 72 excluded at title and abstract; 19 excluded at full assessment; 10 included, of which 6 enter Appendix B.1 and 4 enter Appendix B.2. Twelve of the 29 records taken to full assessment carried no abstract in the export, and full-text retrieval was attempted for each.

| # | Year | First author | Title (truncated) | Type | Decision |
|---|---|---|---|---|---|
| 1 | 1982 | Andrew Pisano | Research progress in industry functional modeling. Final report | article | screening: other |
| 2 | 1990 | H.‐J. Sebastian | System Modelling and Optimization: Proceedings of the 14th Ifip-Conference… | article | screening: not a research output |
| 3 | 1994 | Achim Bachem | Operations research '93 : Extended abstracts of the 18th Symposium on Oper… | article | screening: not a research output |
| 4 | 2002 | Jonathan Bloom | An Application of Self-Organising and Backpropagation Neural Networks for … | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 5 | 2005 | Cao Ting-zhu | Input-output Optimization Model: The development and Innovation Opportunit… | article | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 6 | 2005 | Gao Jun | A multi-objective optimization method of production planning in process ma… | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 7 | 2009 | (none) | Cover | conference-abstract | screening: not a research output |
| 8 | 2010 | Yating Liu | The Energy Conservation and Emission Reduction Dynamic Evolution Model Bas… | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 9 | 2010 | Mark R. Weimar | Using Economic Input/Output Tables to Predict a Country’s Nuclear Status | article | **included, Appendix B.1** |
| 10 | 2011 | Zhaoguang Hu | Study on Agents Response Equilibrium Models | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 11 | 2012 | Justin Kitzes | Quantitative Ecology and the Conservation of Biodiversity: Species Richnes… | dissertation | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 12 | 2013 | Zhaoguang Hu | Updates of the Input–Output Table and the Electricity Input–Output Table | book-chapter | screening: AI named but not applied |
| 13 | 2013 | Виктор Александрович Охонин | План и рынок с позиций математической теории оптимизации | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 14 | 2014 | Dermot Kerr | Modelling and Analysis of Retinal Ganglion Cells with Neural Networks | article | screening: non-economic sense of "input-output" |
| 15 | 2015 | Nicolae Bulz | Five Studies Dedicated to Systems Theory and Cybernetics | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 16 | 2016 | Kristina Lippmann | Altered network oscillations and synaptic plasticity in the blood-brain ba… | dissertation | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 17 | 2016 | Yun Kuen Cheung | A Unified Approach to Analyzing Asynchronous Coordinate Descent and Tatonn… | report | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 18 | 2016 | Yun Kuen Cheung | A Unified Approach to Analyzing Asynchronous Coordinate Descent and Tatonn… | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 19 | 2017 | Jeong-Min Ahn | An Estimation of the Economic Effects of the Healthcare Industry in South … | article | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 20 | 2018 | Nakgyoon Choi | 디지털 혁신의 국제비교와 시나리오별 무역 영향 분석 (International Comparison and Trade Effects o… | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 21 | 2020 | Yu-Hsien Chu | An Economy-Wide Assessment of Artificial Intelligence Investment on Manufa… | article | screening: AI named but not applied |
| 22 | 2020 | Jozef Konings | A roadmap for policy choices after the lock-down: the role of supply chain… | report | screening: AI named but not applied |
| 23 | 2020 | F. Morawski | Neural network reconstruction of the dense matter equation of state derive… | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 24 | 2020 | (none) | Index | paratext | screening: not a research output |
| 25 | 2021 | Murali Krishna Pasupuleti | Quantifying AI’s Socio-Economic Futures: An Uncertainty-Aware Scenario Gen… | article | screening: AI named but not applied |
| 26 | 2021 | (none) | Index | paratext | screening: not a research output |
| 27 | 2022 | Everett Grant | Upstream, Downstream & Common Firm Shocks | preprint | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 28 | 2022 | David F. Hendry | Does an Empirical Economic Relation Have a Life? | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 29 | 2022 | (none) | Index | paratext | screening: not a research output |
| 30 | 2022 | Kai Xiong | Revealing the Semantics of Data Wrangling Scripts With Comantics | article | screening: non-economic sense of "input-output" |
| 31 | 2022 | Vladimir Potashnikоv | Updating of Input-Output tables in Russia by machine learning methods | preprint | **included, Appendix B.1** |
| 32 | 2023 | A. V. Keller | Methods of Automatic and Optimal Control in Dynamic Measurements | article | screening: non-economic sense of "input-output" |
| 33 | 2023 | Shutaro Takeda | Editorial: Sustainametrics: Envisioning a sustainable future with data scie… | editorial | screening: not a research output |
| 34 | 2023 | Enrico Bellino | Reply to Parrinello | letter | screening: AI named but not applied |
| 35 | 2024 | С. И. Носков | Analysis of predictor responses in the Leontief function for fi nancing am… | article | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 36 | 2024 | Rapeeporn Santimalai | Forecasting tourism revenue and evaluating economic impact in Thailand: a … | dataset | excluded at full assessment: learning separated from the IO object by an intervening deterministic model |
| 37 | 2024 | Yanming Guo | ExioML: Eco-economic dataset for Machine Learning in Global Sectoral Susta… | preprint | excluded at full assessment: redundant report, earlier version, or data deposit of an included study |
| 38 | 2024 | Santos, Aécio | GDC-SM: The GDC Schema Matching Benchmark | preprint | screening: non-economic sense of "input-output" |
| 39 | 2025 | Ben-yan TAN | Strong Carbon Leakage and the Improvement of Inter-Provincial Carbon Compe… | preprint | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 40 | 2025 | Jing Wu | A Framework Addressing Supply Chain Carbon Emissions: Measurement, Reporti… | preprint | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 41 | 2025 | anon Flegar | Beyond Reductionism -Exploring AI's First-System Perspective and the Unkno… | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 42 | 2025 | С. И. Носков | IDENTIFICATION OF PARAMETERS OF THE CLUSTER PIECEWISE LINEAR REGRESSION FU… | article | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 43 | 2025 | Murali Kallummal | Legacy Trade Models, Evolving Contours of Regulations, And Growing Digital… | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 44 | 2025 | Nadezhda V. Nasukhanova | APPLICATION OF PRACTICAL CASES OF MATHEMATICAL MODELING FOR FUTURE ECONOMI… | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 45 | 2025 | Janna Axenbeck | Global Embodied Emissions of Digital Technologies: The Hidden 42 % | preprint | screening: IO applied to the footprint of AI itself, out of scope |
| 46 | 2025 | Laura Alfaro | Trade and Industrial Policy in Supply Chains: Directed Technological Chang… | report | screening: AI named but not applied |
| 47 | 2025 | Bing Xia | Non-negligible Unemployment and Economic Losses on Ski Industry in a Warme… | preprint | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 48 | 2025 | Chunhui Huo | Research on the impact of the integration of digital economy and real econ… | article | **included, Appendix B.2** |
| 49 | 2025 | Shuning Zhang | PBE Meets LLM: When Few Examples Aren't Few-Shot Enough | preprint | screening: non-economic sense of "input-output" |
| 50 | 2025 | Janna Axenbeck | Global Embodied Emissions of Digital Technologies: The Hidden 42 % | preprint | screening: IO applied to the footprint of AI itself, out of scope |
| 51 | 2025 | Laura Alfaro | Trade and Industrial Policy in Supply Chains: Directed Technological Chang… | report | screening: AI named but not applied |
| 52 | 2025 | Narinderjit Singh Sawaran Si | AI-driven design and optimization of microwave radiation-induced pyrolysis… | article | screening: non-economic sense of "input-output" |
| 53 | 2025 | Jian Jin (351142) | Input-output table forecasting. | dataset | excluded at full assessment: redundant report, earlier version, or data deposit of an included study |
| 54 | 2025 | Adriana AnaMaria Davidescu | The Effects of Artificial Intelligence Adoption in the Romanian Energy Sec… | article | screening: AI named but not applied |
| 55 | 2025 | Dutta, Ankita | Deep learning models for predicting Toxicity and Bioactivity of the chemic… | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 56 | 2025 | Lihao Lin | Module2 data | dataset | screening: non-economic sense of "input-output" |
| 57 | 2025 | Lihao Lin | Module2 data | dataset | screening: non-economic sense of "input-output" |
| 58 | 2025 | Ishara Mudiyansege | Digital Automation for Scope 3 Emissions Reporting of Complex Value Chains… | conference-paper | **included, Appendix B.1** |
| 59 | 2026 | Dejia Lv | Large Language Models as Processors for Satellite-Derived Bathymetry: A Fo… | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 60 | 2026 | Aditi De | Terminal Sinks: Monetary Circulation Failure as the Primary Economic Risk … | preprint | excluded at full assessment: insufficient metadata after full-text retrieval was attempted, or no learned component on inspection |
| 61 | 2026 | Keith Lambert | The Scarcity Migration Asset Pricing Model: Replacing Historical Covarianc… | preprint | screening: AI named but not applied |
| 62 | 2026 | Voxi Heinrich Amavilah | Choke Points, Concentration, and Systemic Fragility: Theory, Evidence, and… | preprint | screening: AI named but not applied |
| 63 | 2026 | Voxi Heinrich Amavilah | Choke Points, Concentration, and Systemic Fragility: Theory, Evidence, and… | preprint | screening: AI named but not applied |
| 64 | 2026 | Janne M. Korhonen | An empirically grounded modelling architecture for rapid ex ante policy ev… | preprint | screening: AI named but not applied |
| 65 | 2026 | Anh Bui-Tuyet | AI-Driven Energy Efficiency versus AI-Induced Energy Demand: A Dynamic Com… | conference-paper | screening: IO applied to the footprint of AI itself, out of scope |
| 66 | 2026 | Umran Demirors | Artificial Intelligence and Input-Output Analysis: Impacts on Backward and… | preprint | excluded at full assessment: input-output analysis applied to the economic effects of AI, the reverse of the review question |
| 67 | 2026 | Caichun Yin | Data and code for: The dual impact of trade on the water-energy-food nexus… | dataset | **included, Appendix B.2** |
| 68 | 2026 | Caichun Yin | Data and code for: The dual impact of trade on the water-energy-food nexus… | dataset | excluded at full assessment: redundant report, earlier version, or data deposit of an included study |
| 69 | 2026 | Sofia Gratiela BADOI POP | THE IMPACT OF ARTIFICIAL INTELLIGENCE ON STRATEGIC DECISION-MAKING IN MANA… | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 70 | 2026 | Abhimanyu Raj Shekhar | MULTISCALE MODELING APPROACH FOR DESIGN OF INDUSTRIAL NETWORKS TOWARDS ZER… | dissertation | excluded at full assessment: physical input-output tables constructed mechanistically; the learned components act elsewhere |
| 71 | 2026 | Abhimanyu Raj Shekhar | MULTISCALE MODELING APPROACH FOR DESIGN OF INDUSTRIAL NETWORKS TOWARDS ZER… | dissertation | excluded at full assessment: redundant report, earlier version, or data deposit of an included study |
| 72 | 2026 | Matteo Esposito | Replication Package for "Can Large Language Models Judge and Validate Qual… | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 73 | 2026 | Matteo Esposito | Replication Package for "Can Large Language Models Judge and Validate Qual… | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 74 | 2026 | S. Fukui | Enhancing the Accuracy of Regional Input-Output Table Estimation: A Deep L… | preprint | **included, Appendix B.1** |
| 75 | 2026 | S. Fukui | Enhancing the Accuracy of Regional Input-Output Table Estimation: A Deep L… | preprint | excluded at full assessment: redundant report, earlier version, or data deposit of an included study |
| 76 | 2026 | Nazia Riasat | When Stability Fails: Hidden Failure Modes Of LLMS in Data-Constrained Sci… | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 77 | 2026 | Nazia Riasat | When Stability Fails: Hidden Failure Modes Of LLMS in Data-Constrained Sci… | preprint | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 78 | 2026 | Sakayong Pattanavekin | Neuro-Symbolic AI for Hybrid Life Cycle Assessment under Missing Not At Ra… | preprint | **included, Appendix B.1** |
| 79 | 2026 | shijie jiao | "Research on the Impact of Large Model Technology Diffusion on the Innovat… | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 80 | 2026 | Wenrui Yuan | LSTM Baseline | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 81 | 2026 | Wenrui Yuan | LSTM Baseline | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 82 | 2026 | David Lara-Medina | Actualización de una matriz insumo-producto para Jalisco 2018-2023 | dissertation | excluded at full assessment: matrix updated by RAS; the machine-learning term is inherited from the parent project |
| 83 | 2026 | Alex Li | Generation-Verification Asymmetry Inversion and Apprenticeship Pipeline Co… | article | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 84 | 2026 | Fabrizio Fagiolo | Linear Ordering Problem: Time for a Change | preprint | screening: AI named but not applied |
| 85 | 2026 | Simeng Zhang (355579) | Multi-input–output table of PMC model variables for China’s artificial int… | dataset | screening: non-economic sense of "input-output" |
| 86 | 2026 | Yixuan Meng | AI-enabled valuation path optimization for enterprise data assets in urban… | conference-abstract | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 87 | 2026 | Xu Guo | Replication Data and Code for: Typhoon Cloud Morphology as an Early Satell… | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 88 | 2026 | Anh Bui-Tuyet | AI-Driven Energy Efficiency versus AI-Induced Energy Demand: A Dynamic Com… | article | screening: IO applied to the footprint of AI itself, out of scope |
| 89 | 2026 | Zahraa Alkhayat | Machine Learning–Driven Environmentally Extended Input–Output Life Cycle A… | dissertation | **included, Appendix B.1** |
| 90 | 2026 | Y. L. Cui | Intelligent Assessment and Empirical Analysis of the Resilience of Shandon… | article | **included, Appendix B.2** |
| 91 | 2026 | Hong-jin Wang | Code for phenotype-based yield and maturity analysis in foxtail millet | software | screening: non-economic sense of "input-output" |
| 92 | 2026 | Hong-jin Wang | Code for phenotype-based yield and maturity analysis in foxtail millet | software | screening: non-economic sense of "input-output" |
| 93 | 2026 | Muxi Chen | China’sArtificial Intelligence Industry as a Carbon-Linked Production Syst… | article | screening: IO applied to the footprint of AI itself, out of scope |
| 94 | 2026 | Laszlo Pokorny | Foreign Direct Investment Multiplier Effects and Economic Impact Assessmen… | article | screening: AI named but not applied |
| 95 | 2026 | Laszlo Pokorny | Foreign Direct Investment Multiplier Effects and Economic Impact Assessmen… | article | screening: AI named but not applied |
| 96 | 2026 | Tek Kshetri | Dataset and Code for Spatiotemporal Geomorphological Dynamics of Nepalese … | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 97 | 2026 | Tek Kshetri | Dataset and Code for Spatiotemporal Geomorphological Dynamics of Nepalese … | dataset | screening: learned component acts on neither an IO object nor an IO-derived indicator |
| 98 | 2026 | Esteban Fernández Vázquez | Economic and Social Exposure to the Twin Transition: A Multiregional, Mult… | conference-paper | screening: AI named but not applied |
| 99 | 2026 | Esteban Fernández Vázquez | Economic and Social Exposure to the Twin Transition: A Multiregional, Mult… | conference-paper | screening: AI named but not applied |
| 100 | 2026 | Liangcai Zhu | Unveiling non-linear thresholds of life-cycle carbon emissions in small re… | article | **included, Appendix B.2** |
| 101 | n.d. | Tina Highfill | Concepts and Challenges of Measuring Production of Artificial Intelligence… | preprint | screening: AI named but not applied |

---


## Appendix J. Proposals we regard as promising but untested

We record six proposals that no located study has attempted, flagged as speculative and offered because a map listing only what exists is of limited use.

Differentiating an entire compilation pipeline, including balancing, concordance and extension construction, would give exact sensitivities of any published indicator to every upstream choice, and would turn provenance from a label into a quantity. Impact-weighted losses, weighting cell errors by their influence on the indicator of interest, follow from the field-of-influence weights and from the holistic accuracy criterion of Jensen (1980). Learning the reliability weights that KRAS already accepts as inputs would put a statistical footing under a step compilers currently take by judgement: the operator is designed to accept conflicting and unreliable constraints with weights attached (Lenzen, Gallego, & Wood, 2009), and those weights are estimable from revision histories. Active learning over survey and verification budgets, targeting the cells whose measurement would most reduce variance in published indicators, converts an allocation question offices answer by convention into a computable one. Generative table synthesis under hard accounting constraints is the natural extension of §6.2 to modern density models, since denoising diffusion (Ho, Jain, & Abbeel, 2020) admits constrained sampling in a way adversarial training does not. Inverse optimisation applied to the disruptions of 2020 to 2022 could recover the objective functions firms actually pursued; feasibility is low, since firm-level allocation data are required. And low-rank completion over the country-by-sector-by-sector-by-year panel would predict a missing country-year from the structure of the remainder, needing neither margins nor covariates, with applicability depending on Q3.

One proposal in the interface row deserves more than a cell. An agent operating an IO model through its own interface would have to do four things a scripted pipeline does not: select a construct and valuation basis and state the choice; refuse a query the accounts cannot answer, such as a physical inference from a monetary table; carry provenance from cell to result so that a model-imputed input is visible in the output; and report the invariance checks of §9.1 alongside the number. The first and second are the hard ones, and they are questions about the accounts rather than about the agent. We record this because the capability will be built whether or not the field specifies it, and specification is cheaper before the fact.

---


## References

Abdella, G. M., Kucukvar, M., Onat, N. C., Al-Yafay, H. M., & Bulak, M. E. (2020). Sustainability assessment and modeling based on supervised machine learning techniques: The case for food consumption. *Journal of Cleaner Production, 251*, 119661. https://doi.org/10.1016/j.jclepro.2019.119661

Acemoglu, D., Carvalho, V. M., Ozdaglar, A., & Tahbaz-Salehi, A. (2012). The network origins of aggregate fluctuations. *Econometrica, 80*(5), 1977–2016. https://doi.org/10.3982/ECTA9623

Agrawal, A., Amos, B., Barratt, S., Boyd, S., Diamond, S., & Kolter, J. Z. (2019). Differentiable convex optimization layers. In *Advances in Neural Information Processing Systems 32* (pp. 9558–9570). Curran Associates. https://proceedings.neurips.cc/paper/2019/hash/9ce3c52fc54362e22053399d3181c638-Abstract.html

Alkhayat, Z. (2026). *Machine learning-driven environmentally extended input–output life cycle assessment of greenhouse gas emissions in Saudi Arabia* [Doctoral dissertation, King Abdullah University of Science and Technology]. https://doi.org/10.25781/kaust-q725c

Alleman, T. W., Schoors, K., & Baetens, J. M. (2023). *Validating a dynamic input–output model for the propagation of supply and demand shocks during the COVID-19 pandemic in Belgium* (arXiv:2305.16377). arXiv. https://arxiv.org/abs/2305.16377

Almon, C. (2000). Product-to-product tables via product-technology with no negative flows. *Economic Systems Research, 12*(1), 27–43. https://doi.org/10.1080/095353100111263

Amos, B., & Kolter, J. Z. (2017). OptNet: Differentiable optimization as a layer in neural networks. In *Proceedings of the 34th International Conference on Machine Learning* (Proceedings of Machine Learning Research, Vol. 70, pp. 136–145). PMLR. https://proceedings.mlr.press/v70/amos17a.html

An, P., Qu, S., Yu, K., & Xu, M. (2024). Mapping analytical methods between input–output economics and network science. *Journal of Industrial Ecology, 28*(4), 648–679. https://doi.org/10.1111/jiec.13493

André, M., Bourgeois, A., Combet, E., Lequien, M., & Pottier, A. (2024). Challenges in measuring the distribution of carbon footprints: The role of product and price heterogeneity. *Ecological Economics, 220*, Article 108122. https://doi.org/10.1016/j.ecolecon.2024.108122

André, M., Mach, R., & Weinzettel, J. (2024). Price heterogeneity and the distributional incidence of consumption-based carbon footprints. *Ecological Economics*. Advance online publication.

Angelopoulos, A. N., & Bates, S. (2023). Conformal prediction: A gentle introduction. *Foundations and Trends in Machine Learning, 16*(4), 494–591. https://doi.org/10.1561/2200000101

Balaji, B., Guest, G., Vunnava, V. S. G., & Kramer, J. (2023). CaML: Carbon footprinting of household products with zero-shot semantic text similarity. In *Proceedings of the ACM Web Conference 2023*. Association for Computing Machinery. https://doi.org/10.1145/3543507.3583882

Barber, R. F., Candès, E. J., Ramdas, A., & Tibshirani, R. J. (2021). The limits of distribution-free conditional predictive inference. *Information and Inference: A Journal of the IMA, 10*(2), 455–482. https://doi.org/10.1093/imaiai/iaaa017

Baydin, A. G., Pearlmutter, B. A., Radul, A. A., & Siskind, J. M. (2018). Automatic differentiation in machine learning: A survey. *Journal of Machine Learning Research, 18*(153), 1–43. https://jmlr.org/papers/v18/17-468.html

Benhari, M. A., Kaicer, M., & Driss, B. (2026). Resolution of linear interval systems using neural networks and their application to the Leontief economic model. *Statistics, Optimization and Information Computing, 15*(2), 1357–1369. https://doi.org/10.19139/soic-2310-5070-2778

Bonfiglio, A., & Chelli, F. (2008). Assessing the behaviour of non-survey methods for constructing regional input–output tables through a Monte Carlo simulation. *Economic Systems Research, 20*(3), 243–258. https://doi.org/10.1080/09535310802344315

Bouwmeester, M. C., & Oosterhaven, J. (2013). Specification and aggregation errors in environmentally extended input–output models. *Environmental and Resource Economics, 56*(3), 307–335. https://doi.org/10.1007/s10640-013-9649-8

Bródy, A. (1997). The second eigenvalue of the Leontief matrix. *Economic Systems Research, 9*(3), 253–258. https://doi.org/10.1080/09535319700000018

Breiman, L. (2001). Random forests. *Machine Learning, 45*(1), 5–32. https://doi.org/10.1023/A:1010933404324

Brown, T. B., Mann, B., Ryder, N., Subbiah, M., Kaplan, J., Dhariwal, P., Neelakantan, A., Shyam, P., Sastry, G., Askell, A., Agarwal, S., Herbert-Voss, A., Krueger, G., Henighan, T., Child, R., Ramesh, A., Ziegler, D. M., Wu, J., Winter, C., … Amodei, D. (2020). Language models are few-shot learners. In *Advances in Neural Information Processing Systems 33*. Curran Associates. https://proceedings.neurips.cc/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html

Bullard, C. W., & Sebald, A. V. (1977). Effects of parametric uncertainty and technological change on input-output models. *The Review of Economics and Statistics, 59*(1), 75–81. https://doi.org/10.2307/1924906

Bullard, C. W., & Sebald, A. V. (1988). Monte Carlo sensitivity analysis of input-output models. *The Review of Economics and Statistics, 70*(4), 708–712. https://doi.org/10.2307/1935838

Bustos, S., Jackson, E., Torun, D., Leonard, B., Tuzcu, N., Lukaszuk, P., White, A., Hausmann, R., & Yıldırım, M. A. (2026). Tackling discrepancies in trade data: The Harvard Growth Lab international trade datasets. *Scientific Data, 13*, Article 170. https://doi.org/10.1038/s41597-025-06488-2

Chen, G., Zhu, Y., Wiedmann, T., Yao, L., Xu, L., & Wang, Y. (2019). Urban-rural disparities of household energy requirements and influence factors in China: Classification tree models. *Applied Energy, 250*, 1321–1335. https://doi.org/10.1016/j.apenergy.2019.04.170

Chen, H., Constante Flores, G. E., & Li, C. (2024). Physics-informed neural networks with hard linear equality constraints. *Computers & Chemical Engineering, 189*, Article 108764. https://doi.org/10.1016/j.compchemeng.2024.108764

Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. In *Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining* (pp. 785–794). Association for Computing Machinery. https://doi.org/10.1145/2939672.2939785

Chen, T. Y., Kuo, F.-C., Liu, H., Poon, P.-L., Towey, D., Tse, T. H., & Zhou, Z. Q. (2018). Metamorphic testing: A review of challenges and opportunities. *ACM Computing Surveys, 51*(1), 1–27. https://doi.org/10.1145/3143561

Cui, Y. L., & Ma, L. (2026). Intelligent assessment and empirical analysis of the resilience of Shandong Province's manufacturing industry chain under the impact of tariff policies. *Advanced Electromagnetics, 15*(3). https://doi.org/10.7716/aem.v15i3.3757

Cullen, L., Marinoni, A., & Cullen, J. M. (2024). Machine learning for gap-filling in greenhouse gas emissions databases. *Journal of Industrial Ecology, 28*(4), 636–647. https://doi.org/10.1111/jiec.13507

Cuturi, M. (2013). Sinkhorn distances: Lightspeed computation of optimal transport. In *Advances in Neural Information Processing Systems 26*. Curran Associates. https://proceedings.neurips.cc/paper/2013/hash/af21d0c97db2e27e13572cbf59eb343d-Abstract.html

de Mesnard, L. (2011). Negatives in symmetric input–output tables: The impossible quest for the Holy Grail. *The Annals of Regional Science, 46*(2), 427–454. https://doi.org/10.1007/s00168-009-0332-5

De Pretis, F., Tortoli, D., & Caria, S. (2026). Keeping up with the regions: A hybrid machine learning framework for estimating regional input–output tables. *Scientific Reports, 16*, Article 10893. https://doi.org/10.1038/s41598-026-45382-8

Demirors, U., Coskun, O., & Ulger, C. (2026). *Artificial intelligence and input-output analysis: Impacts on backward and forward sectoral linkages* [Working paper]. SSRN. https://doi.org/10.2139/ssrn.7277318

Diem, C., Borsos, A., Reisch, T., Kertész, J., & Thurner, S. (2022). Quantifying firm-level economic systemic risk from nation-wide supply networks. *Scientific Reports, 12*, Article 7719. https://doi.org/10.1038/s41598-022-11522-z

Dietzenbacher, E., & Los, B. (1998). Structural decomposition techniques: Sense and sensitivity. *Economic Systems Research, 10*(4), 307–324. https://doi.org/10.1080/09535319800000023

Dietzenbacher, E. (1990). The sensitivity of input–output multipliers. *Journal of Regional Science, 30*(2), 239–258. https://doi.org/10.1111/j.1467-9787.1990.tb00095.x

Dietzenbacher, E. (1997). In vindication of the Ghosh model: A reinterpretation as a price model. *Journal of Regional Science, 37*(4), 629–651. https://doi.org/10.1111/0022-4146.00073

Dietzenbacher, E. (2005). Waste treatment in physical input–output analysis. *Ecological Economics, 55*(1), 11–23. https://doi.org/10.1016/j.ecolecon.2005.04.009

Dietzenbacher, E., Giljum, S., Hubacek, K., & Suh, S. (2009). Physical input-output analysis and disposals to nature. In S. Suh (Ed.), *Handbook of input-output economics in industrial ecology* (pp. 123–137). Springer. https://doi.org/10.1007/978-1-4020-5737-3_7

Donti, P. L., Rolnick, D., & Kolter, J. Z. (2021). DC3: A learning method for optimization with hard constraints. In *9th International Conference on Learning Representations*.

Duchin, F., & Levine, S. H. (2011). Sectors may use multiple technologies simultaneously: The rectangular choice-of-technology model with binding factor constraints. *Economic Systems Research, 23*(3), 281–302. https://doi.org/10.1080/09535314.2011.571238

Duchin, F., & Levine, S. H. (2012). The rectangular sector-by-technology model: Not every economy produces every product and some products may rely on several technologies simultaneously. *Journal of Economic Structures, 1*, Article 3. https://doi.org/10.1186/2193-2409-1-3

Duchin, F., & Levine, S. H. (2016). Combining multiregional input–output analysis with a world trade model for evaluating scenarios for sustainable use of global resources, Part II: Implementation. *Journal of Industrial Ecology, 20*(4), 775–782. https://doi.org/10.1111/jiec.12302

Duchin, F., & Szyld, D. B. (1985). A dynamic input–output model with assured positive output. *Metroeconomica, 37*(3), 269–282. https://doi.org/10.1111/j.1467-999X.1985.tb00414.x

Duchin, F. (2005). A world trade model based on comparative advantage with m regions, n goods, and k factors. *Economic Systems Research, 17*(2), 141–162. https://doi.org/10.1080/09535310500114903

Dumit, A., Rao, K., Kwee, T., Gopalakrishnan, V., Tsai, K., & Suh, S. (2024). *ATLAS: A spend classification benchmark for estimating scope 3 carbon emissions* [Paper presentation]. NeurIPS 2024 Workshop on Tackling Climate Change with Machine Learning. https://www.climatechange.ai/papers/neurips2024/70

Dumpert, F. (Ed.). (2025). *Foundations and advances of machine learning in official statistics*. Springer. https://doi.org/10.1007/978-3-032-10004-7

Fang, C., Cheng, J., You, Z., Chen, J., & Peng, J. (2023). A detailed examination of China's clean energy mineral consumption: Footprints, trends, and drivers. *Sustainability, 15*(23), 16255. https://doi.org/10.3390/su152316255

Faridzad, A. (2025). Applying machine learning to input–output analysis: A new perspective on identifying key Australian industries. *Journal of Economic Structures, 14*(1), 1–27. https://doi.org/10.1186/s40008-025-00351-8

Faridzad, A. (2026). Financial sector linkages and real economy impacts in Malaysia: Evidence from a machine learning approach. *Asian Development Review, 43*(1), 139–168. https://doi.org/10.1142/S0116110525500325

Fazal, R., Ma, Y., Baynes, T., & Lenzen, M. (2026). Estimating concordance matrices using artificial intelligence. *Economic Systems Research, 38*(3), 330–344. https://doi.org/10.1080/09535314.2026.2635628

Fessina, M., Cimini, G., Squartini, T., Astudillo-Estévez, P., Thurner, S., & Garlaschelli, D. (2026). Inferring firm-level supply chain networks with realistic systemic risk from industry sector-level data. *Scientific Reports, 16*, Article 19848. https://doi.org/10.1038/s41598-026-47883-y

Flegg, A. T., & Tohmo, T. (2013). A comment on Tobias Kronenberg's "Construction of regional input–output tables using nonsurvey methods: The role of cross-hauling". *International Regional Science Review, 36*(2), 235–257. https://doi.org/10.1177/0160017612446371

Flegg, A. T., & Tohmo, T. (2013). Regional input–output tables and the FLQ formula: A case study of Finland. *Regional Studies, 47*(5), 703–721. https://doi.org/10.1080/00343404.2011.592138

Flegg, A. T., & Webber, C. D. (2000). Regional size, regional specialization and the FLQ formula. *Regional Studies, 34*(6), 563–569. https://doi.org/10.1080/00343400050085675

Flegg, A. T., Mastronardi, L. J., & Romero, C. A. (2016). Evaluating the FLQ and AFLQ formulae for estimating regional input coefficients: Empirical evidence for the province of Córdoba, Argentina. *Economic Systems Research, 28*(1), 21–37. https://doi.org/10.1080/09535314.2015.1103703

Flegg, A. T., Webber, C. D., & Elliott, M. V. (1995). On the appropriate use of location quotients in generating regional input–output tables. *Regional Studies, 29*(6), 547–561. https://doi.org/10.1080/00343409512331349173

Friedman, J. H. (2001). Greedy function approximation: A gradient boosting machine. *The Annals of Statistics, 29*(5), 1189–1232. https://doi.org/10.1214/aos/1013203451

Fukui, S. (2025). Estimating input coefficients for regional input–output tables using deep learning with mixup. *Computational Economics, 65*(4), 2423–2448. https://doi.org/10.1007/s10614-024-10641-1

Fukui, S. (2026). *Enhancing the accuracy of regional input-output table estimation: A deep learning approach* (arXiv:2603.13823). arXiv. https://arxiv.org/abs/2603.13823

Furtado, B. A., & Andreão, G. O. (2022). *Machine learning simulates agent-based model towards policy* (arXiv:2203.02576). arXiv. https://arxiv.org/abs/2203.02576

Gal, Y., & Ghahramani, Z. (2016). Dropout as a Bayesian approximation: Representing model uncertainty in deep learning. In *Proceedings of the 33rd International Conference on Machine Learning* (Proceedings of Machine Learning Research, Vol. 48, pp. 1050–1059). PMLR. https://proceedings.mlr.press/v48/gal16.html

Ge, Y., Qu, J., Huang, K., Han, J., Maraseni, T. N., Liu, L., Xu, L., Wang, D., Zeng, J., Li, H., Pei, H., & Gao, X. (2026). Disparities in household carbon emissions across urban–rural and regional dimensions: Evidence from large-scale field surveys. *Energy Economics, 158*, 109327. https://doi.org/10.1016/j.eneco.2026.109327

Ge, Z., Yan, C., Guo, J., & Zhang, C. (2026). Evaluating the embodied carbon emissions of power infrastructure construction towards carbon neutrality: A study of Fujian province, China. *Energy Strategy Reviews, 64*, Article 102096. https://doi.org/10.1016/j.esr.2026.102096

Giljum, S., & Hubacek, K. (2009). Conceptual foundations and applications of physical input-output tables. In S. Suh (Ed.), *Handbook of input-output economics in industrial ecology* (pp. 61–75). Springer. https://doi.org/10.1007/978-1-4020-5737-3_4

Giljum, S., Wieland, H., Lutter, S., Eisenmenger, N., Schandl, H., & Owen, A. (2019). The impacts of data deviations between MRIO models on material footprints: A comparison of EXIOBASE, Eora, and ICIO. *Journal of Industrial Ecology, 23*(4), 946–958. https://doi.org/10.1111/jiec.12833

Gilmer, J., Schoenholz, S. S., Riley, P. F., Vinyals, O., & Dahl, G. E. (2017). Neural message passing for quantum chemistry. In *Proceedings of the 34th International Conference on Machine Learning* (Proceedings of Machine Learning Research, Vol. 70, pp. 1263–1272). PMLR. https://proceedings.mlr.press/v70/gilmer17a.html

Gong, Y., Ma, F., Wang, H., Tzachor, A., Sun, W., Zhu, J., Liu, G., & Schandl, H. (2025). The evolution of research at the intersection of industrial ecology and artificial intelligence. *Journal of Industrial Ecology, 29*(2), 440–457. https://doi.org/10.1111/jiec.13612

Goodfellow, I., Bengio, Y., & Courville, A. (2016). *Deep learning*. The MIT Press.

Goodfellow, I., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A., & Bengio, Y. (2014). Generative adversarial nets. In *Advances in Neural Information Processing Systems 27* (pp. 2672–2680). Curran Associates. https://proceedings.neurips.cc/paper/2014/hash/5ca3e9b122f61f8f06494c97b1afccf3-Abstract.html

Grant, M. J., & Booth, A. (2009). A typology of reviews: An analysis of 14 review types and associated methodologies. *Health Information & Libraries Journal, 26*(2), 91–108. https://doi.org/10.1111/j.1471-1842.2009.00848.x

Griewank, A., & Walther, A. (2008). *Evaluating derivatives: Principles and techniques of algorithmic differentiation* (2nd ed.). Society for Industrial and Applied Mathematics. https://doi.org/10.1137/1.9780898717761

Gu, F., Chang, H., Zhu, W., Sojoudi, S., & El Ghaoui, L. (2020). Implicit graph neural networks. In *Advances in Neural Information Processing Systems 33*. Curran Associates. https://proceedings.neurips.cc/paper/2020/hash/8b5c8441a8ff8e151b191c53c1842a38-Abstract.html

Guo, C., Pleiss, G., Sun, Y., & Weinberger, K. Q. (2017). On calibration of modern neural networks. In *Proceedings of the 34th International Conference on Machine Learning* (Proceedings of Machine Learning Research, Vol. 70, pp. 1321–1330). PMLR. https://proceedings.mlr.press/v70/guo17a.html

Guo, Y., Guan, C., & Ma, J. (2024). *ExioML: Eco-economic dataset for machine learning in global sectoral sustainability* (arXiv:2406.09046). arXiv. https://arxiv.org/abs/2406.09046

Guo, Y., Guan, C., & Ma, J. (2026). Global emission factor dataset for Scope 3 machine learning applications. *Scientific Data, 13*(1). https://doi.org/10.1038/s41597-026-06699-1

Guo, Y., Qian, X., Credit, K., & Ma, J. (2025). *Group reasoning emission estimation networks* (arXiv:2502.06874). arXiv. https://arxiv.org/abs/2502.06874

Hallegatte, S. (2008). An adaptive regional input–output model and its application to the assessment of the economic cost of Katrina. *Risk Analysis, 28*(3), 779–799. https://doi.org/10.1111/j.1539-6924.2008.01046.x

Hallegatte, S. (2014). Modeling the role of inventories and heterogeneity in the assessment of the economic costs of natural disasters. *Risk Analysis, 34*(1), 152–167. https://doi.org/10.1111/risa.12090

Han, G., Tang, L., & Liu, Z.-M. (2024). How does regional integration affect carbon emission transfer? Evidence from the Yangtze River Delta, China. *Resources and Environment in the Yangtze Basin, 33*(10), 2271–2284. https://doi.org/10.11870/cjlyzyyhj202410016

Hastie, T., Tibshirani, R., & Friedman, J. (2009). *The elements of statistical learning* (2nd ed.). Springer. https://doi.org/10.1007/978-0-387-84858-7

He, K., Mi, Z., & Guan, D. (2025). *Leveraging machine learning in input-output economic modeling* [Conference paper]. 31st International Input-Output Conference, Malé, Maldives. International Input-Output Association. https://www.iioa.org/conferences/31st/papers/files/5363_MLIOTmanuscript-IIOA.pdf

Hewings, G. J. D., Sonis, M., & Jensen, R. C. (1988). Fields of influence of technological change in input–output models. *Papers in Regional Science, 64*(1), 25–36. https://doi.org/10.1111/j.1435-5597.1988.tb01112.x

Ho, J., Jain, A., & Abbeel, P. (2020). Denoising diffusion probabilistic models. In *Advances in Neural Information Processing Systems 33*. Curran Associates. https://proceedings.neurips.cc/paper/2020/hash/4c5bcfec8584af0d967f1ab10179ca4b-Abstract.html

Hou, X., Zheng, J., He, M., Feng, G., He, K., Ma, T., Coffman, D., Mi, Z., & Wang, S. (2025). A multi-regional input-output database linking Chinese subnational regions and global economies. *Scientific Data, 12*(1), 1761. https://doi.org/10.1038/s41597-025-06040-2

Hubacek, K., & Giljum, S. (2003). Applying physical input–output analysis to estimate land appropriation (ecological footprints) of international trade activities. *Ecological Economics, 44*(1), 137–151. https://doi.org/10.1016/S0921-8009(02)00257-4

Huo, C., Bian, S., He, D., & Lv, M. (2025). Research on the impact of the integration of digital economy and real economy on China's domestic value chain resilience. *Digital Economy and Sustainable Development, 3*(1), Article 4. https://doi.org/10.1007/s44265-025-00064-7

Huo, J., Chen, P., Hubacek, K., Zheng, H., Meng, J., & Guan, D. (2022). Full-scale, near real-time multi-regional input–output table for the global emerging economies (EMERGING). *Journal of Industrial Ecology, 26*(4), 1218–1232. https://doi.org/10.1111/jiec.13264

Ito, Y. (2000). Adaptive dynamic input-output analysis using neural networks: Japanese industrial structure. *Kybernetes, 29*(9/10), 1087–1102. https://doi.org/10.1108/03684920010342152

Jensen, R. C. (1980). The concept of accuracy in regional input–output models. *International Regional Science Review, 5*(2), 139–154. https://doi.org/10.1177/016001768000500203

Jin, J., & Zhang, M. (2025). Dynamic supply-side multipliers in China's marine economy: A neural network-enhanced Ghosh model for sustainable development. *PLOS ONE*. https://doi.org/10.1371/journal.pone.0334336

Junius, T., & Oosterhaven, J. (2003). The solution of updating or regionalizing a matrix with both positive and negative entries. *Economic Systems Research, 15*(1), 87–96. https://doi.org/10.1080/0953531032000056954

Kapoor, S., & Narayanan, A. (2023). Leakage and the reproducibility crisis in machine-learning-based science. *Patterns, 4*(9), Article 100804. https://doi.org/10.1016/j.patter.2023.100804

Kapoor, S., Cantrell, E. M., Peng, K., Pham, T. H., Bail, C. A., Gundersen, O. E., Hofman, J. M., Hullman, J., Lones, M. A., Malik, M. M., Nanayakkara, P., Poldrack, R. A., Raji, I. D., Roberts, M., Salganik, M. J., Serra-Garcia, M., Stewart, B. M., Vandewiele, G., & Narayanan, A. (2024). REFORMS: Consensus-based recommendations for machine-learning-based science. *Science Advances, 10*(18), Article eadk3452. https://doi.org/10.1126/sciadv.adk3452

Karbevska, L., & Hidalgo, C. A. (2025). Mapping global value chains at the product level. *EPJ Data Science, 14*, 44. https://doi.org/10.1140/epjds/s13688-025-00521-5

Karniadakis, G. E., Kevrekidis, I. G., Lu, L., Perdikaris, P., Wang, S., & Yang, L. (2021). Physics-informed machine learning. *Nature Reviews Physics, 3*(6), 422–440. https://doi.org/10.1038/s42254-021-00314-5

Karstensen, J., Peters, G. P., & Andrew, R. M. (2015). Uncertainty in temperature response of current consumption-based emissions estimates. *Earth System Dynamics, 6*(1), 287–309. https://doi.org/10.5194/esd-6-287-2015

Kim, H., Choi, J.-K., & Hong, T. (2026). Construction supply-chain carbon footprint with graph neural network-based input–output framework. *Building and Environment, 303*, Article 114904. https://doi.org/10.1016/j.buildenv.2026.114904

Kipf, T. N., & Welling, M. (2017). Semi-supervised classification with graph convolutional networks. In *5th International Conference on Learning Representations*.

Kleinberg, J., & Raghavan, M. (2021). Algorithmic monoculture and social welfare. *Proceedings of the National Academy of Sciences, 118*(22), Article e2018340118. https://doi.org/10.1073/pnas.2018340118

Klicpera, J., Bojchevski, A., & Günnemann, S. (2019). Predict then propagate: Graph neural networks meet personalized PageRank. In *7th International Conference on Learning Representations*.

Koks, E. E., & Thissen, M. (2016). A multiregional impact assessment model for disaster analysis. *Economic Systems Research, 28*(4), 429–449. https://doi.org/10.1080/09535314.2016.1232701

Konstantakis, K. N., Cheilas, P. T., Melissaropoulos, I. G., Xidonas, P., & Michaelides, P. G. (2023). Supply chains and fake news: A novel input–output neural network approach for the US food sector. *Annals of Operations Research, 327*(2), 779–794. https://doi.org/10.1007/s10479-022-04812-2

Kop Jansen, P., & ten Raa, T. (1990). The choice of model in the construction of input–output coefficients matrices. *International Economic Review, 31*(1), 213–227. https://doi.org/10.2307/2526639

Kovanda, J., Weinzettel, J., & Hak, T. (2018). Analysis of raw material equivalents of Czech foreign trade. *Journal of Industrial Ecology*. https://doi.org/10.1111/jiec.12694

Kovanda, J., Weinzettel, J., & Schoer, K. (2018). What makes the difference in raw material equivalents calculation through environmentally extended input-output analysis? *Ecological Economics, 149*, 80–87. https://doi.org/10.1016/j.ecolecon.2018.03.004

Kronenberg, T. (2009). Construction of regional input–output tables using nonsurvey methods: The role of cross-hauling. *International Regional Science Review, 32*(1), 40–64. https://doi.org/10.1177/0160017608322555

Köse, S., Diem, C., Dervic, E., Friesenbichler, K., Heiler, G., Hurt, J., Picatto, H., & Klimek, P. (2026). *Reconstructing temporal multi-relational firm networks at scale using large language models* (arXiv:2605.15842). arXiv. https://arxiv.org/abs/2605.15842

Lahr, M. L., & Stevens, B. H. (2002). A study of the role of regionalization in the generation of aggregation error in regional input–output models. *Journal of Regional Science, 42*(3), 477–507. https://doi.org/10.1111/1467-9787.00268

Lahr, M. L. (1993). A review of the literature supporting the hybrid approach to constructing regional input–output models. *Economic Systems Research, 5*(3), 277–293. https://doi.org/10.1080/09535319300000023

Lam, R., Sanchez-Gonzalez, A., Willson, M., Wirnsberger, P., Fortunato, M., Alet, F., Ravuri, S., Ewalds, T., Eaton-Rosen, Z., Hu, W., Merose, A., Hoyer, S., Holland, G., Vinyals, O., Stott, J., Pritzel, A., Mohamed, S., & Battaglia, P. (2023). Learning skillful medium-range global weather forecasting. *Science, 382*(6677), 1416–1421. https://doi.org/10.1126/science.adi2336

Lara-Medina, D., Ruiz-González, D., & Alejandre-DelÁngel, N. A. (2026). *Actualización de una matriz insumo-producto para Jalisco 2018-2023* [Professional application project report]. Instituto Tecnológico y de Estudios Superiores de Occidente. https://rei.iteso.mx/items/e566071d-d590-4e23-bf8e-f0fe16afd030

LeCun, Y., Bengio, Y., & Hinton, G. (2015). Deep learning. *Nature, 521*(7553), 436–444. https://doi.org/10.1038/nature14539

Lenzen, M., & Dey, C. (2000). Truncation error in embodied energy analyses of basic iron and steel products. *Energy, 25*(6), 577–585. https://doi.org/10.1016/S0360-5442(99)00088-2

Lenzen, M., & Reynolds, C. J. (2014). A supply-use approach to waste input-output analysis. *Journal of Industrial Ecology, 18*(2), 212–226. https://doi.org/10.1111/jiec.12105

Lenzen, M., & Rueda-Cantuche, J. M. (2012). A note on the use of supply-use tables in impact analyses. *SORT: Statistics and Operations Research Transactions, 36*(2), 139–152.

Lenzen, M. (2000). Errors in conventional and input-output-based life-cycle inventories. *Journal of Industrial Ecology, 4*(4), 127–148. https://doi.org/10.1162/10881980052541981

Lenzen, M. (2003). Environmentally important paths, linkages and key sectors in the Australian economy. *Structural Change and Economic Dynamics, 14*(1), 1–34. https://doi.org/10.1016/S0954-349X(02)00025-5

Lenzen, M. (2009). Dealing with double-counting in tiered hybrid life-cycle inventories: A few comments. *Journal of Cleaner Production, 17*(15), 1382–1384. https://doi.org/10.1016/j.jclepro.2009.03.005

Lenzen, M. (2011). Aggregation versus disaggregation in input–output analysis of the environment. *Economic Systems Research, 23*(1), 73–89. https://doi.org/10.1080/09535314.2010.548793

Lenzen, M., Gallego, B., & Wood, R. (2009). Matrix balancing under conflicting information. *Economic Systems Research, 21*(1), 23–44. https://doi.org/10.1080/09535310802688661

Lenzen, M., Geschke, A., Abd Rahman, M. D., Xiao, Y., Fry, J., Reyes, R., Dietzenbacher, E., Inomata, S., Kanemoto, K., Los, B., Moran, D., Schulte in den Bäumen, H., Tukker, A., Walmsley, T., Wiedmann, T., Wood, R., & Yamano, N. (2017). The Global MRIO Lab, charting the world economy. *Economic Systems Research, 29*(2), 158–186. https://doi.org/10.1080/09535314.2017.1301887

Lenzen, M., Geschke, A., West, J., Fry, J., Malik, A., Giljum, S., Milà i Canals, L., Piñero, P., Lutter, S., Wiedmann, T., Li, M., Sevenster, M., Potočnik, J., Teixeira, I., Van Voore, M., Nansai, K., & Schandl, H. (2022). Implementing the material footprint to measure progress towards Sustainable Development Goals 8 and 12. *Nature Sustainability, 5*(2), 157–166. https://doi.org/10.1038/s41893-021-00811-6

Lenzen, M., Kanemoto, K., Moran, D., & Geschke, A. (2012). Mapping the structure of the world economy. *Environmental Science & Technology, 46*(15), 8374–8381. https://doi.org/10.1021/es300171x

Lenzen, M., Moran, D., Bhaduri, A., Kanemoto, K., Bekchanov, M., Geschke, A., & Foran, B. (2013). International trade of scarce water. *Ecological Economics, 94*, 78–85. https://doi.org/10.1016/j.ecolecon.2013.06.018

Lenzen, M., Moran, D., Kanemoto, K., & Geschke, A. (2013). Building Eora: A global multi-region input–output database at high country and sector resolution. *Economic Systems Research, 25*(1), 20–49. https://doi.org/10.1080/09535314.2013.769938

Lenzen, M., Moran, D., Kanemoto, K., Foran, B., Lobefaro, L., & Geschke, A. (2012). International trade drives biodiversity threats in developing nations. *Nature, 486*(7401), 109–112. https://doi.org/10.1038/nature11145

Lenzen, M., Wood, R., & Gallego, B. (2007). Some comments on the GRAS method. *Economic Systems Research, 19*(4), 461–465. https://doi.org/10.1080/09535310701698613

Lenzen, M., Wood, R., & Wiedmann, T. (2010). Uncertainty analysis for multi-region input–output models, A case study of the UK's carbon footprint. *Economic Systems Research, 22*(1), 43–63. https://doi.org/10.1080/09535311003661226

Leontief, W. (1970). The dynamic inverse. In A. P. Carter & A. Bródy (Eds.), *Contributions to input–output analysis* (pp. 17–46). North-Holland.

Leontief, W. W. (1936). Quantitative input and output relations in the economic systems of the United States. *The Review of Economics and Statistics, 18*(3), 105–125. https://doi.org/10.2307/1927837

Leontief, W. W. (1941). *The structure of American economy, 1919–1929: An empirical application of equilibrium analysis*. Harvard University Press.

Lewis, P., Perez, E., Piktus, A., Petroni, F., Karpukhin, V., Goyal, N., Küttler, H., Lewis, M., Yih, W., Rocktäschel, T., Riedel, S., & Kiela, D. (2020). Retrieval-augmented generation for knowledge-intensive NLP tasks. In *Advances in Neural Information Processing Systems 33*. Curran Associates. https://proceedings.neurips.cc/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html

Li, M., Ingwersen, W. W., Young, B., Vendries, J., & Birney, C. (2022). useeior: An open-source R package for building and using US environmentally-extended input–output models. *Applied Sciences, 12*(9), Article 4469. https://doi.org/10.3390/app12094469

Li, M., Tong, Y., Zhu, J., & Xu, S. (2024). A high-resolution multi-scale industrial water use dataset in China. *Scientific Data, 11*(1), 1–12. https://doi.org/10.1038/s41597-024-04204-0

Li, M., Wiedmann, T., & Hadjikakou, M. (2019). Towards meaningful consumption-based planetary boundary indicators: The phosphorus exceedance footprint. *Global Environmental Change, 54*, 227–238. https://doi.org/10.1016/j.gloenvcha.2018.12.005

Li, Q., Han, Z., & Wu, X.-M. (2018). Deeper insights into graph convolutional networks for semi-supervised learning. *Proceedings of the AAAI Conference on Artificial Intelligence, 32*(1). https://doi.org/10.1609/aaai.v32i1.11604

Li, S., Li, Y., Huang, G., Wang, P., & Li, Y. (2026). An input–output analysis CNN-LSTM model for analyzing the virtual water consumption. In *Environmental science and engineering* (pp. 179–187). Springer. https://doi.org/10.1007/978-3-032-15080-6_14

Li, S. Z., Li, Y. P., Huang, G. H., Wang, P. P., Liu, J. T., Xu, Z. P., & Li, Y. F. (2026). Coupling input-output analysis with deep learning to quantify the carrying capacity of water resource for sustainable development in arid region. *Journal of Cleaner Production, 560*, 148356. https://doi.org/10.1016/j.jclepro.2026.148356

Li, W., Liu, X., Yuan, X., & Lu, C. (2024). Impact of CBAM on carbon emission reduction in global steel foreign trade: Projections based on the embodied carbon emission intensity of major countries. *Energy Sources, Part B: Economics, Planning and Policy, 19*(1), 2360443. https://doi.org/10.1080/15567249.2024.2360443

Li, W., Zhang, H., Hu, J., & Zuo, F. (2024). Research on the influence of inter-industry cascade relationships based on reinforcement learning. In *Proceedings of the 2024 International Conference on Artificial Intelligence, Big Data and Algorithms* (pp. 436–440). Association for Computing Machinery. https://doi.org/10.1145/3690407.3690481

Lillicrap, T. P., Hunt, J. J., Pritzel, A., Heess, N., Erez, T., Tassa, Y., Silver, D., & Wierstra, D. (2016). Continuous control with deep reinforcement learning. In *4th International Conference on Learning Representations*. https://arxiv.org/abs/1509.02971

Liu, D., Liang, J., Xu, S., & Ye, M. (2023). Analysis of carbon emissions embodied in the provincial trade of China based on an input–output model and k-means algorithm. *Sustainability, 15*(12), 9196. https://doi.org/10.3390/su15129196

Liu, D., Liang, J., Zhou, J., Xu, S., Ye, M., & Liu, Z. (2025). Regional differences reflected in resource flow in China: Multidimensional analysis integrating MRIO and machine learning clustering. *ACS Sustainable Chemistry & Engineering, 13*(24), 8878–8893. https://doi.org/10.1021/acssuschemeng.4c09911

Liu, H. (2026). A data-driven framework for enterprise management using system dynamics, machine learning, and computational modeling. *AIP Advances, 16*(7), 075207. https://doi.org/10.1063/5.0341166

Liu, X., Moreno, B., & García, A. S. (2016). A grey neural network and input-output combined forecasting model: Primary energy consumption forecasts in Spanish economic sectors. *Energy, 115*, 1042–1054. https://doi.org/10.1016/j.energy.2016.09.017

Lloyd, S. P. (1982). Least squares quantization in PCM. *IEEE Transactions on Information Theory, 28*(2), 129–137. https://doi.org/10.1109/TIT.1982.1056489

Lundberg, S. M., & Lee, S.-I. (2017). A unified approach to interpreting model predictions. In *Advances in Neural Information Processing Systems 30* (pp. 4765–4774). Curran Associates. https://proceedings.neurips.cc/paper/2017/hash/8a20a8621978632d76c43dfd28b67767-Abstract.html

Ma, Z., Liu, J., Li, Y., Zhang, H., & Fang, L. (2023). A BPNN-based ecologically extended input–output model for virtual water metabolism network management of Kazakhstan. *Environmental Science and Pollution Research, 30*(15), 43752–43767. https://doi.org/10.1007/s11356-023-25280-6

Mach, R., Ščasný, M., & Weinzettel, J. (2022). The role of allocation of retail trade margins across household segments on their carbon footprint calculation. *Economic Systems Research, 34*(1), 97–110. https://doi.org/10.1080/09535314.2020.1855418

Majeau-Bettez, G., Wood, R., & Strømman, A. H. (2014). Unified theory of allocations and constructs in life cycle assessment and input–output analysis. *Journal of Industrial Ecology, 18*(5), 747–770. https://doi.org/10.1111/jiec.12142

Mensikova, A., Rizzo, D. M., & Hinkelman, K. (2026). *Mapping the landscape of artificial intelligence in life cycle assessment using large language models* (arXiv:2602.22500). arXiv. https://arxiv.org/abs/2602.22500

Merciai, S., & Schmidt, J. (2018). Methodology for the construction of global multi-regional hybrid supply and use tables for the EXIOBASE v3 database. *Journal of Industrial Ecology, 22*(3), 516–531. https://doi.org/10.1111/jiec.12713

Miller, R. E., & Blair, P. D. (2022). *Input–output analysis: Foundations and extensions* (3rd ed.). Cambridge University Press. https://doi.org/10.1017/9781108676212

Molladavoudi, S., & Yung, W. (2023). Exploring quality dimensions in trustworthy machine learning in the context of official statistics: Model explainability and uncertainty quantification. *AStA Wirtschafts- und Sozialstatistisches Archiv, 17*, 265–284. https://doi.org/10.1007/s11943-023-00325-x

Moran, D., & Belaid, M.-B. (2026). *Machine learning predictions of GDP at higher spatial and sectoral resolution* [Conference abstract]. 32nd International Input-Output Conference & 11th SHAIO Conference, Seville, Spain. International Input-Output Association. https://www.iioa.org/conferences/32nd/papers/files/5524.pdf

Moran, D., & Wood, R. (2014). Convergence between the Eora, WIOD, EXIOBASE, and OpenEU's consumption-based carbon accounts. *Economic Systems Research, 26*(3), 245–261. https://doi.org/10.1080/09535314.2014.935298

Mudiyansege, I., Kumari, K., Pepper, M., McDowell, C., & De Zoysa, A. (2025). Digital automation for Scope 3 emissions reporting of complex value chains: A machine learning based approach. In *Proceedings of the 4th Australian International Conference on Industrial Engineering and Operations Management*. IEOM Society International. https://doi.org/10.46254/au04.20250113

Mungo, L., Lafond, F., Astudillo-Estévez, P., & Farmer, J. D. (2023). Reconstructing production networks using machine learning. *Journal of Economic Dynamics and Control, 148*, Article 104607. https://doi.org/10.1016/j.jedc.2023.104607

Munn, Z., Peters, M. D. J., Stern, C., Tufanaru, C., McArthur, A., & Aromataris, E. (2018). Systematic review or scoping review? Guidance for authors when choosing between a systematic or scoping review approach. *BMC Medical Research Methodology, 18*(1), Article 143. https://doi.org/10.1186/s12874-018-0611-x

Ohsato, T., Akagi, K., & Deguchi, H. (2018). Developing an input-output table generation algorithm using a Japanese trade database: Dealing with ambiguous export and import information. In *New frontiers in artificial intelligence* (Lecture Notes in Computer Science, Vol. 10838, pp. 83–96). Springer. https://doi.org/10.1007/978-3-319-93794-6_6

Oosterhaven, J., & Bouwmeester, M. C. (2016). A new approach to modeling the impact of disruptive events. *Journal of Regional Science, 56*(4), 583–595. https://doi.org/10.1111/jors.12262

Oosterhaven, J., & Többen, J. (2017). Wider economic impacts of heavy flooding in Germany: A non-linear programming approach. *Spatial Economic Analysis, 12*(4), 404–428. https://doi.org/10.1080/17421772.2017.1300680

Oosterhaven, J. (1988). On the plausibility of the supply-driven input–output model. *Journal of Regional Science, 28*(2), 203–217. https://doi.org/10.1111/j.1467-9787.1988.tb01208.x

Oosterhaven, J. (2012). Adding supply-driven consumption makes the Ghosh model even more implausible. *Economic Systems Research, 24*(1), 101–111. https://doi.org/10.1080/09535314.2011.635137

Oosterhaven, J. (2017). On the limited usability of the inoperability IO model. *Economic Systems Research, 29*(3), 452–461. https://doi.org/10.1080/09535314.2017.1301395

Oosterhaven, J. (2022). *Rethinking input–output analysis: A spatial perspective* (2nd ed.). Springer. https://doi.org/10.1007/978-3-031-05087-9

Owen, A., Steen-Olsen, K., Barrett, J., Wiedmann, T., & Lenzen, M. (2014). A structural decomposition approach to comparing MRIO databases. *Economic Systems Research, 26*(3), 262–283. https://doi.org/10.1080/09535314.2014.935299

Owen, A., Wood, R., Barrett, J., & Evans, A. (2016). Explaining value chain differences in MRIO databases through structural path decomposition. *Economic Systems Research, 28*(2), 243–272. https://doi.org/10.1080/09535314.2015.1135309

Page, M. J., McKenzie, J. E., Bossuyt, P. M., Boutron, I., Hoffmann, T. C., Mulrow, C. D., Shamseer, L., Tetzlaff, J. M., Akl, E. A., Brennan, S. E., Chou, R., Glanville, J., Grimshaw, J. M., Hróbjartsson, A., Lalu, M. M., Li, T., Loder, E. W., Mayo-Wilson, E., McDonald, S., … Moher, D. (2021). The PRISMA 2020 statement: An updated guideline for reporting systematic reviews. *BMJ, 372*, Article n71. https://doi.org/10.1136/bmj.n71

Pakizeh, A. H., & Kashani, H. (2022). Application of machine-learning models to estimate regional input coefficients and multipliers. *Spatial Economic Analysis, 17*(2), 178–205. https://doi.org/10.1080/17421772.2021.1959046

Pan, S. J., & Yang, Q. (2010). A survey on transfer learning. *IEEE Transactions on Knowledge and Data Engineering, 22*(10), 1345–1359. https://doi.org/10.1109/TKDE.2009.191

Pang, Z., & Kong, Y. (2022). Prediction of household carbon emissions based on SP-LIME and ensemble learning models. In *2022 IEEE 5th International Conference on Electronics Technology* (pp. 650–654). IEEE. https://doi.org/10.1109/ICET55676.2022.9825391

Papadas, C. T., & Hutchinson, W. G. (2002). Neural network forecasts of input-output technology. *Applied Economics, 34*(13), 1607–1615. https://doi.org/10.1080/00036840110118133

Pattanavekin, S., & Ekgasit, S. (2026). *Neuro-symbolic AI for hybrid life cycle assessment under missing not at random data: Inventory completion from electronic tax records* [Preprint]. Research Square. https://doi.org/10.21203/rs.3.rs-9052200/v1

Pauliuk, S., & Heeren, N. (2020). ODYM, An open software framework for studying dynamic material systems: Principles, implementation, and data structures. *Journal of Industrial Ecology, 24*(3), 446–458. https://doi.org/10.1111/jiec.12952

Peters, J., Janzing, D., & Schölkopf, B. (2017). *Elements of causal inference: Foundations and learning algorithms*. The MIT Press.

Pichler, A., Pangallo, M., del Rio-Chanona, R. M., Lafond, F., & Farmer, J. D. (2022). Forecasting the propagation of pandemic shocks with a dynamic input–output model. *Journal of Economic Dynamics and Control, 144*, Article 104527. https://doi.org/10.1016/j.jedc.2022.104527

Potashnikov, V. (2022). *Updating of input-output tables in Russia by machine learning methods* [Preprint]. Zenodo. https://doi.org/10.5281/zenodo.7426951

Quandt, R. E. (1959). On the solution of probabilistic Leontief systems. *Naval Research Logistics Quarterly, 6*(4), 295–305. https://doi.org/10.1002/nav.3800060405

Raissi, M., Perdikaris, P., & Karniadakis, G. E. (2019). Physics-informed neural networks: A deep learning framework for solving forward and inverse problems involving nonlinear partial differential equations. *Journal of Computational Physics, 378*, 686–707. https://doi.org/10.1016/j.jcp.2018.10.045

Rodrigues, J. F. D. (2014). A Bayesian approach to the balancing of statistical economic data. *Entropy, 16*(3), 1243–1271. https://doi.org/10.3390/e16031243

Rodrigues, J. F. D. (2016). Maximum-entropy prior uncertainty and correlation of statistical economic data. *Journal of Business & Economic Statistics, 34*(3), 357–367. https://doi.org/10.1080/07350015.2015.1038545

Rodrigues, J. F. D., Moran, D., Wood, R., & Behrens, P. (2018). Uncertainty of consumption-based carbon accounts. *Environmental Science & Technology, 52*(13), 7577–7586. https://doi.org/10.1021/acs.est.8b00632

Round, J. I. (1983). Nonsurvey techniques: A critical review of the theory and the evidence. *International Regional Science Review, 8*(3), 189–212. https://doi.org/10.1177/016001768300800302

Round, J. I. (2003). Constructing SAMs for development policy analysis: Lessons learned and challenges ahead. *Economic Systems Research, 15*(2), 161–183. https://doi.org/10.1080/0953531032000091153

Rueda-Cantuche, J. M., & ten Raa, T. (2009). The choice of model in the construction of industry coefficients matrices. *Economic Systems Research, 21*(4), 363–376. https://doi.org/10.1080/09535310903208344

Rueda-Cantuche, J. M., & ten Raa, T. (2013). Testing assumptions made in the construction of input–output tables. *Economic Systems Research, 25*(2), 170–189. https://doi.org/10.1080/09535314.2013.774265

Saliminezhad, A., & Lisaniler, F. G. (2018). Validity of unbalanced growth theory and sectoral investment priorities in Indonesia: Application of feature ranking methods. *Journal of International Trade and Economic Development, 27*(5), 521–540. https://doi.org/10.1080/09638199.2017.1398270

Schulte, S., Jakobs, A., & Pauliuk, S. (2024). Estimating the uncertainty of the greenhouse gas emission accounts in global multi-regional input–output analysis. *Earth System Science Data, 16*(6), 2669–2700. https://doi.org/10.5194/essd-16-2669-2024

Shumailov, I., Shumaylov, Z., Zhao, Y., Papernot, N., Anderson, R., & Gal, Y. (2024). AI models collapse when trained on recursively generated data. *Nature, 631*(8022), 755–759. https://doi.org/10.1038/s41586-024-07566-y

Sinkhorn, R., & Knopp, P. (1967). Concerning nonnegative matrices and doubly stochastic matrices. *Pacific Journal of Mathematics, 21*(2), 343–348. https://doi.org/10.2140/pjm.1967.21.343

Sonis, M., & Hewings, G. J. D. (1992). Coefficient change in input–output models: Theory and applications. *Economic Systems Research, 4*(2), 143–158. https://doi.org/10.1080/09535319200000013

Stadler, K. (2021). Pymrio, A Python based multi-regional input-output analysis toolbox. *Journal of Open Research Software, 9*(1), Article 8. https://doi.org/10.5334/jors.251

Stadler, K., Wood, R., Bulavskaya, T., Södersten, C.-J., Simas, M., Schmidt, S., Usubiaga, A., Acosta-Fernández, J., Kuenen, J., Bruckner, M., Giljum, S., Lutter, S., Merciai, S., Schmidt, J. H., Theurl, M. C., Plutzar, C., Kastner, T., Eisenmenger, N., Erb, K.-H., de Koning, A., & Tukker, A. (2018). EXIOBASE 3: Developing a time series of detailed environmentally extended multi-regional input-output tables. *Journal of Industrial Ecology, 22*(3), 502–515. https://doi.org/10.1111/jiec.12715

Steen-Olsen, K., Owen, A., Hertwich, E. G., & Lenzen, M. (2014). Effects of sector aggregation on CO₂ multipliers in multiregional input–output analyses. *Economic Systems Research, 26*(3), 284–302. https://doi.org/10.1080/09535314.2014.934325

Su, B., & Ang, B. W. (2010). Input–output analysis of CO₂ emissions embodied in trade: The effects of spatial aggregation. *Ecological Economics, 70*(1), 10–18. https://doi.org/10.1016/j.ecolecon.2010.08.016

Suh, S., Weidema, B., Schmidt, J. H., & Heijungs, R. (2010). Generalized make and use framework for allocation in life cycle assessment. *Journal of Industrial Ecology, 14*(2), 335–353. https://doi.org/10.1111/j.1530-9290.2010.00235.x

Sun, G.-Z. (2008). The first two eigenvalues of large random matrices and Brody's hypothesis on the stability of large input–output systems. *Economic Systems Research, 20*(4), 429–432. https://doi.org/10.1080/09535310802551471

Többen, J., & Kronenberg, T. H. (2015). Construction of multi-regional input–output tables using the CHARM method. *Economic Systems Research, 27*(4), 487–507. https://doi.org/10.1080/09535314.2015.1091765

Temurshoev, U., & Oosterhaven, J. (2014). Analytical and empirical comparison of policy-relevant key sector measures. *Spatial Economic Analysis, 9*(3), 284–308. https://doi.org/10.1080/17421772.2014.930168

Temurshoev, U., Miller, R. E., & Bouwmeester, M. C. (2013). A note on the GRAS method. *Economic Systems Research, 25*(3), 361–367. https://doi.org/10.1080/09535314.2012.746645

Temurshoev, U., Webb, C., & Yamano, N. (2011). Projection of supply and use tables: Methods and their empirical assessment. *Economic Systems Research, 23*(1), 91–123. https://doi.org/10.1080/09535314.2010.534978

ten Raa, T., & Rueda-Cantuche, J. M. (2003). The construction of input–output coefficients matrices in an axiomatic context: Some further considerations. *Economic Systems Research, 15*(4), 439–455. https://doi.org/10.1080/0953531032000152317

ten Raa, T., & Rueda-Cantuche, J. M. (2013). The problem of negatives generated by the commodity technology model in input–output analysis: A review of the solutions. *Journal of Economic Structures, 2*, Article 5. https://doi.org/10.1186/2193-2409-2-5

ten Raa, T. (2005). *The economics of input–output analysis*. Cambridge University Press. https://doi.org/10.1017/CBO9780511610783

Tibshirani, R. J., Barber, R. F., Candès, E. J., & Ramdas, A. (2019). Conformal prediction under covariate shift. In *Advances in Neural Information Processing Systems 32* (pp. 2526–2536). Curran Associates. https://proceedings.neurips.cc/paper/2019/hash/8fb21ee7a2207526da55a679f0332de2-Abstract.html

Torres-González, L. D., & Yang, J. (2019). The persistent statistical structure of the US input–output coefficient matrices: 1963–2007. *Economic Systems Research, 31*(4), 481–504. https://doi.org/10.1080/09535314.2018.1561425

Tranos, E., Carrascal-Incera, A., & Willis, G. (2023). Using the web to predict regional trade flows: Data extraction, modeling, and validation. *Annals of the American Association of Geographers, 113*(3), 717–739. https://doi.org/10.1080/24694452.2022.2109577

Trase. (2026, March 3). *AI maps 9,300 Brazilian soy facilities, unlocking supply chain traceability* [Press release]. https://trase.earth/media/press-release/ai-maps-9-300-brazilian-soy-facilities-unlocking-supply-chain-traceability

Tricco, A. C., Lillie, E., Zarin, W., O'Brien, K. K., Colquhoun, H., Levac, D., Moher, D., Peters, M. D. J., Horsley, T., Weeks, L., Hempel, S., Akl, E. A., Chang, C., McGowan, J., Stewart, L., Hartling, L., Aldcroft, A., Wilson, M. G., Garritty, C., ... Straus, S. E. (2018). PRISMA extension for scoping reviews (PRISMA-ScR): Checklist and explanation. *Annals of Internal Medicine, 169*(7), 467–473. https://doi.org/10.7326/M18-0850

Tsionas, M. G. (2020). Bayesian input–output table update using a benchmark LASSO prior. *Economic Systems Research, 32*(3), 413–427. https://doi.org/10.1080/09535314.2019.1707170

United Nations Economic Commission for Europe. (2021). *Machine learning for official statistics* (HLG-MOS Machine Learning Project). United Nations. https://unece.org/statistics/documents/2021/12/machine-learning-official-statistics

United Nations, European Commission, Food and Agriculture Organization of the United Nations, International Monetary Fund, Organisation for Economic Co-operation and Development, & World Bank. (2014). *System of environmental-economic accounting 2012, Central framework* (ST/ESA/STAT/Ser.F/109). United Nations. https://seea.un.org/content/seea-central-framework

Valderas-Jaramillo, J. M., Rueda-Cantuche, J. M., Olmedo, E., & Beutel, J. (2019). Projecting supply and use tables: New variants and fair comparisons. *Economic Systems Research, 31*(3), 423–444. https://doi.org/10.1080/09535314.2018.1545221

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is all you need. In *Advances in Neural Information Processing Systems 30*. Curran Associates. https://proceedings.neurips.cc/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html

Vovk, V., Gammerman, A., & Shafer, G. (2005). *Algorithmic learning in a random world*. Springer. https://doi.org/10.1007/b106715

Wang, B., & Zhou, Q. (2020). Prediction and comparison of the impact of the COVID-19 epidemic on the financial industry of major countries based on a neural intelligent algorithm. *Journal of Intelligent & Fuzzy Systems, 39*(6), 8831–8838. https://doi.org/10.3233/JIFS-189280

Wang, L., Zheng, H., Chen, Y., Hu, X., & Ouyang, Z. (2026). An integrated method to account for river flood mitigation service in the SEEA-EA framework. *Ecosystem Services, 77*, 101803. https://doi.org/10.1016/j.ecoser.2025.101803

Wang, P. P., Huang, G. H., Li, Y. P., Zhang, Y. F., Cai, T. C., Song, T. N., Liu, Y. Y., Xu, Z. P., & Shen, Z. Y. (2024). Unveiling key drivers of economy-water system and transforming water use pattern into sustainable development: Inner-Shaan-Ning region in the Yellow River Basin. *Journal of Cleaner Production, 475*, 143651. https://doi.org/10.1016/j.jclepro.2024.143651

Wang, S. (2001). The neural network approach to input–output analysis for economic systems. *Neural Computing & Applications, 10*(1), 22–28. https://doi.org/10.1007/s005210170014

Weimar, M. R., Daly, D. S., & Wood, T. W. (2010). *Using economic input/output tables to predict a country's nuclear status* (PNNL-SA-73279). In *Proceedings of the 51st Annual Meeting of the Institute of Nuclear Materials Management*. Pacific Northwest National Laboratory. https://www.pnnl.gov/publications/using-economic-inputoutput-tables-predict-countrys-nuclear-status

Weinzettel, J., Hertwich, E. G., Peters, G. P., Steen-Olsen, K., & Galli, A. (2013). Affluence drives the global displacement of land use. *Global Environmental Change, 23*(2), 433–438. https://doi.org/10.1016/j.gloenvcha.2012.12.010

Weisz, H., & Duchin, F. (2006). Physical and monetary input–output analysis: What makes the difference? *Ecological Economics, 57*(3), 534–541. https://doi.org/10.1016/j.ecolecon.2005.05.011

West, G. R. (1986). A stochastic analysis of an input-output model. *Econometrica, 54*(2), 363–374. https://doi.org/10.2307/1913156

Wiedmann, T., & Lenzen, M. (2018). Environmental and social footprints of international trade. *Nature Geoscience, 11*(5), 314–321. https://doi.org/10.1038/s41561-018-0113-9

Wiedmann, T. (2009). A review of recent multi-region input–output models used for consumption-based emission and resource accounting. *Ecological Economics, 69*(2), 211–222. https://doi.org/10.1016/j.ecolecon.2009.08.026

Wiedmann, T. O., Schandl, H., Lenzen, M., Moran, D., Suh, S., West, J., & Kanemoto, K. (2015). The material footprint of nations. *Proceedings of the National Academy of Sciences, 112*(20), 6271–6276. https://doi.org/10.1073/pnas.1220362110

Wilting, H. C. (2012). Sensitivity and uncertainty analysis in MRIO modelling; Some empirical results with regard to the Dutch carbon footprint. *Economic Systems Research, 24*(2), 141–171. https://doi.org/10.1080/09535314.2011.628302

Wilting, H. C., Schipper, A. M., Bakkenes, M., Meijer, J. R., & Huijbregts, M. A. J. (2017). Quantifying biodiversity losses due to human consumption: A global-scale footprint analysis. *Environmental Science & Technology, 51*(6), 3298–3306. https://doi.org/10.1021/acs.est.6b05296

Wood, R., & Lenzen, M. (2009). Structural path decomposition. *Energy Economics, 31*(3), 335–341. https://doi.org/10.1016/j.eneco.2008.11.003

Wu, F., Souza, A., Zhang, T., Fifty, C., Yu, T., & Weinberger, K. (2019). Simplifying graph convolutional networks. In *Proceedings of the 36th International Conference on Machine Learning* (Proceedings of Machine Learning Research, Vol. 97, pp. 6861–6871). PMLR. https://proceedings.mlr.press/v97/wu19e.html

Xu, K., Hu, W., Leskovec, J., & Jegelka, S. (2019). How powerful are graph neural networks? In *7th International Conference on Learning Representations*.

Xu, L., Skoularidou, M., Cuesta-Infante, A., & Veeramachaneni, K. (2019). Modeling tabular data using conditional GAN. In *Advances in Neural Information Processing Systems 32*. Curran Associates. https://proceedings.neurips.cc/paper/2019/hash/254ed7d2de3b23ab10936522dd547b78-Abstract.html

Xu, Y., & Zhang, T. (2009). A new approach to modeling waste in physical input–output analysis. *Ecological Economics, 68*(10), 2475–2478. https://doi.org/10.1016/j.ecolecon.2009.04.010

Yamano, N., Alsamawi, A., Webb, C., Cimper, A., Zürcher, C., & Chiapin Pechansky, R. (2023). *Development of the OECD inter-country input-output database 2023* (OECD Science, Technology and Industry Working Papers No. 2023/08). OECD Publishing. https://doi.org/10.1787/5a5d0665-en

Yin, C., Zhao, W., Fu, B., Pereira, P., Meadows, M. E., Ding, J., & Liu, J. (2026). The dual impact of trade on the water–energy–food nexus globally. *Nature Sustainability, 9*(6), 921–932. https://doi.org/10.1038/s41893-026-01796-w

Yu, Y., Wang, X., Manya, D., & Hsu, A. (2026). Machine learning estimates for G20 subnational urban greenhouse gas emissions from 2000 to 2020. *Scientific Data*. Advance online publication. https://doi.org/10.1038/s41597-026-06691-9

Zhang, D., Caron, J., & Winchester, N. (2019). Sectoral aggregation error in the accounting of energy and emissions embodied in trade and consumption. *Journal of Industrial Ecology, 23*(2), 402–411. https://doi.org/10.1111/jiec.12734

Zhang, H., Cissé, M., Dauphin, Y. N., & Lopez-Paz, D. (2018). mixup: Beyond empirical risk minimization. In *6th International Conference on Learning Representations*. https://arxiv.org/abs/1710.09412

Zhang, Z., Li, Y., Lai, D., Zhou, N., Zhan, Q., & Wang, W. (2026). Unveiling Scope 3 emissions in energy supply chains: A graph neural network approach for missing data imputation and optimization. *Frontiers in Energy Research, 14*, 1811386. https://doi.org/10.3389/fenrg.2026.1811386

Zhao, B., Jiang, J., Xu, M., & Tu, Q. (2025). A data-centric investigation on the challenges of machine learning methods for bridging life cycle inventory data gaps. *Journal of Industrial Ecology, 29*, 955–966. https://doi.org/10.1111/jiec.70022

Zhao, B., Shuai, C., Qu, S., & Xu, M. (2022). Using deep learning to fill data gaps in environmental footprint accounting. *Environmental Science & Technology, 56*(16), 11897–11906. https://doi.org/10.1021/acs.est.2c01640

Zhao, L., & He, Z. (2026a). Global maritime embedded carbon flow network: Key factors and formation mechanism. *Transportation Research Part E: Logistics and Transportation Review, 207*, 104647. https://doi.org/10.1016/j.tre.2025.104647

Zhao, L., & He, Z. (2026b). The impact of inter-country differences on transportation carbon emission transfer. *Transport Policy, 179*, 104006. https://doi.org/10.1016/j.tranpol.2026.104006

Zheng, C., Zheng, Z., Lin, H., Liu, M., & Wu, Q. (2026). Input-output sensitivity analysis model construction and multi-objective weight adjustment. *Proceedings of SPIE, 14142*, 141420G. https://doi.org/10.1117/12.3107609

Zhi, J., Yu, Y., Zeng, Q., Shi, C., Chen, S., & Wang, Y. (2023). Multi-scale near-long-range flow measurement and analysis of virtual water in China based on multi-regional input-output model and machine learning. *Process Safety and Environmental Protection, 175*, 854–869. https://doi.org/10.1016/j.psep.2023.06.007

Zhou, B., Li, Y., Ding, Y., Huang, G., & Shen, Z. (2023). An input-output-based Bayesian neural network method for analyzing carbon reduction potential: A case study of Guangdong province. *Journal of Cleaner Production, 389*, 135986. https://doi.org/10.1016/j.jclepro.2023.135986

Zhu, L., Yang, Y., & Li, Z. (2026). Unveiling non-linear thresholds of life-cycle carbon emissions in small reservoirs: An integrated stochastic EI-LCA and machine learning framework. *Environmental Science and Pollution Research*. https://doi.org/10.1007/s11356-026-38137-5

Zou, Y., Li, Y., & Han, Z. (2025). Spatiotemporal evolution and drivers of the carbon footprint and embodied carbon transfer in the advanced manufacturing industry: Case study of the western region in China. *Sustainability, 17*(22), 10272. https://doi.org/10.3390/su172210272

Zou, Y., Li, Y., & Han, Z. (2026). Reconstruction and forecasting of carbon footprints and embodied transfers in advanced manufacturing: A hybrid WOA-GNN framework applied to western China. *Networks and Spatial Economics, 26*(2), 813–853. https://doi.org/10.1007/s11067-026-09736-z
