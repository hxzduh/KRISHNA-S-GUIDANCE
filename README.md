# KRISHNA-S-GUIDANCE
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bhagavad Gita Wisdom Cards</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 40px;
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .emotions-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .emotion-card {
            background: white;
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            cursor: pointer;
            transform: translateY(0);
            transition: all 0.3s ease;
            border-left: 8px solid;
            position: relative;
            overflow: hidden;
        }

        .emotion-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .emotion-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: inherit;
        }

        .sad { border-left-color: #4CAF50; background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%); }
        .jealous { border-left-color: #FFC107; background: linear-gradient(135deg, #FFC107 0%, #ffb300 100%); }
        .angry { border-left-color: #F44336; background: linear-gradient(135deg, #F44336 0%, #d32f2f 100%); }
        .fearful { border-left-color: #9C27B0; background: linear-gradient(135deg, #9C27B0 0%, #7b1fa2 100%); }
        .confused { border-left-color: #FF9800; background: linear-gradient(135deg, #FF9800 0%, #f57c00 100%); }
        .anxious { border-left-color: #E91E63; background: linear-gradient(135deg, #E91E63 0%, #c2185b 100%); }
        .peaceful { border-left-color: #2196F3; background: linear-gradient(135deg, #2196F3 0%, #1976d2 100%); }
        .motivated { border-left-color: #FF5722; background: linear-gradient(135deg, #FF5722 0%, #d84315 100%); }

        .emotion-card h3 {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: white;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
        }

        .emotion-card p {
            color: rgba(255,255,255,0.9);
            margin-bottom: 15px;
        }

        .shloka-count {
            background: rgba(255,255,255,0.2);
            padding: 5px 12px;
            border-radius: 20px;
            color: white;
            font-size: 0.9rem;
            display: inline-block;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
            animation: fadeIn 0.3s ease;
        }

        .modal-content {
            position: relative;
            background: white;
            margin: 5% auto;
            padding: 0;
            width: 90%;
            max-width: 800px;
            border-radius: 20px;
            max-height: 80vh;
            overflow-y: auto;
            animation: slideIn 0.3s ease;
        }

        .modal-header {
            padding: 25px;
            border-radius: 20px 20px 0 0;
            color: white;
            position: relative;
        }

        .close {
            position: absolute;
            right: 20px;
            top: 20px;
            color: white;
            font-size: 30px;
            cursor: pointer;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255,255,255,0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 0.3s ease;
        }

        .close:hover {
            background: rgba(255,255,255,0.3);
        }

        .modal-body {
            padding: 30px;
        }

        .shloka-card {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 20px;
            border-left: 5px solid;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .shloka-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .shloka-sanskrit {
            font-size: 1.2rem;
            color: #333;
            font-weight: bold;
            margin-bottom: 15px;
            line-height: 1.6;
            font-family: serif;
        }

        .shloka-translation {
            color: #666;
            font-size: 1rem;
            line-height: 1.6;
            margin-bottom: 10px;
        }

        .shloka-reference {
            font-size: 0.9rem;
            color: #888;
            font-style: italic;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @media (max-width: 768px) {
            .header h1 { font-size: 2rem; }
            .emotions-grid { grid-template-columns: 1fr; }
            .modal-content { margin: 10% auto; width: 95%; }
        }

        .floating-om {
            position: fixed;
            color: rgba(255,255,255,0.1);
            font-size: 100px;
            z-index: -1;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }
    </style>
</head>
<body>
    <div class="floating-om" style="top: 10%; left: 5%;">ॐ</div>
    <div class="floating-om" style="top: 60%; right: 5%; animation-delay: -2s;">ॐ</div>
    <div class="floating-om" style="top: 80%; left: 20%; animation-delay: -4s;">ॐ</div>

    <div class="container">
        <div class="header">
            <h1>🕉️ Bhagavad Gita Wisdom Cards</h1>
            <p>Find guidance through timeless wisdom - Choose the emotion that resonates with your heart</p>
        </div>

        <div class="emotions-grid">
            <div class="emotion-card sad" onclick="openModal('sad')">
                <h3>😢 Feeling Sad</h3>
                <p>When sorrow weighs heavy on your heart, find solace in Krishna's eternal wisdom</p>
                <span class="shloka-count">5 Shlokas</span>
            </div>

            <div class="emotion-card jealous" onclick="openModal('jealous')">
                <h3>😤 Feeling Jealous</h3>
                <p>Transform envy into understanding through divine teachings on contentment</p>
                <span class="shloka-count">4 Shlokas</span>
            </div>

            <div class="emotion-card angry" onclick="openModal('angry')">
                <h3>😠 Feeling Angry</h3>
                <p>Channel your anger into righteous action and inner peace</p>
                <span class="shloka-count">6 Shlokas</span>
            </div>

            <div class="emotion-card fearful" onclick="openModal('fearful')">
                <h3>😰 Feeling Fearful</h3>
                <p>Conquer fear through faith and understanding of the eternal self</p>
                <span class="shloka-count">5 Shlokas</span>
            </div>

            <div class="emotion-card confused" onclick="openModal('confused')">
                <h3>🤔 Feeling Confused</h3>
                <p>Clear the clouds of doubt with the light of divine knowledge</p>
                <span class="shloka-count">7 Shlokas</span>
            </div>

            <div class="emotion-card anxious" onclick="openModal('anxious')">
                <h3>😟 Feeling Anxious</h3>
                <p>Find calm in the storm through surrender and trust in the divine plan</p>
                <span class="shloka-count">4 Shlokas</span>
            </div>

            <div class="emotion-card peaceful" onclick="openModal('peaceful')">
                <h3>🕊️ Seeking Peace</h3>
                <p>Deepen your tranquility through contemplation of the eternal truths</p>
                <span class="shloka-count">6 Shlokas</span>
            </div>

            <div class="emotion-card motivated" onclick="openModal('motivated')">
                <h3>🔥 Seeking Motivation</h3>
                <p>Ignite your inner fire with teachings on righteous duty and action</p>
                <span class="shloka-count">5 Shlokas</span>
            </div>
        </div>
    </div>

    <!-- Modal -->
    <div id="modal" class="modal" onclick="closeModal(event)">
        <div class="modal-content" onclick="event.stopPropagation()">
            <div id="modal-header" class="modal-header">
                <span class="close" onclick="closeModal()">&times;</span>
                <h2 id="modal-title"></h2>
                <p id="modal-subtitle"></p>
            </div>
            <div class="modal-body">
                <div id="shlokas-container"></div>
            </div>
        </div>
    </div>

    <script>
        const emotionData = {
            sad: {
                title: "😢 Guidance for Sadness",
                subtitle: "Let these verses comfort your grieving heart",
                color: "linear-gradient(135deg, #4CAF50 0%, #45a049 100%)",
                shlokas: [
                    {
                        sanskrit: "गतासूनगतासूंश्च नानुशोचन्ति पण्डिताः।",
                        translation: "The wise grieve neither for the living nor the dead. Just as a person puts on new garments, giving up old ones, the soul similarly accepts new material bodies, giving up the old and useless ones.",
                        reference: "Bhagavad Gita 2.11"
                    },
                    {
                        sanskrit: "वासांसि जीर्णानि यथा विहाय नवानि गृह्णाति नरोऽपराणि।",
                        translation: "As a person sheds worn-out garments and takes other new ones, so does the soul cast off worn-out bodies and take others that are new.",
                        reference: "Bhagavad Gita 2.22"
                    },
                    {
                        sanskrit: "न जायते म्रियते वा कदाचिन्नायं भूत्वा भविता वा न भूयः।",
                        translation: "For the soul there is never birth nor death. It is not slain when the body is slain. The soul is unborn, eternal, permanent, and primeval.",
                        reference: "Bhagavad Gita 2.20"
                    },
                    {
                        sanskrit: "अशोच्यानन्वशोचस्त्वं प्रज्ञावादांश्च भाषसे।",
                        translation: "While speaking learned words, you are mourning for what is not worthy of grief. Those who are wise lament neither for the living nor the dead.",
                        reference: "Bhagavad Gita 2.11"
                    },
                    {
                        sanskrit: "मात्रास्पर्शास्तु कौन्तेय शीतोष्णसुखदुःखदाः।",
                        translation: "O son of Kunti, the contact between the senses and the sense objects gives rise to fleeting perceptions of happiness and distress. These are non-permanent, and one must learn to tolerate them without being disturbed.",
                        reference: "Bhagavad Gita 2.14"
                    }
                ]
            },
            jealous: {
                title: "😤 Overcoming Jealousy",
                subtitle: "Transform envy into contentment and understanding",
                color: "linear-gradient(135deg, #FFC107 0%, #ffb300 100%)",
                shlokas: [
                    {
                        sanskrit: "सन्तुष्टः सततं योगी यतात्मा दृढनिश्चयः।",
                        translation: "Always satisfied, self-controlled, and of firm determination, with mind and intelligence fixed on Me, such a devotee of Mine is very dear to Me.",
                        reference: "Bhagavad Gita 12.14"
                    },
                    {
                        sanskrit: "यस्त्वात्मरतिरेव स्यादात्मतृप्तश्च मानवः।",
                        translation: "One who is satisfied in the self, who is self-content, and who finds pleasure within the self alone, for him there is nothing more to be accomplished.",
                        reference: "Bhagavad Gita 3.17"
                    },
                    {
                        sanskrit: "अद्वेष्टा सर्वभूतानां मैत्रः करुण एव च।",
                        translation: "One who is not envious but is a kind friend to all living entities, who does not think himself a proprietor and is free from false ego, who is equal in both happiness and distress, who is tolerant, always satisfied, self-controlled, and engaged in devotional service with determination, his mind and intelligence fixed on Me—such a devotee of Mine is very dear to Me.",
                        reference: "Bhagavad Gita 12.13"
                    },
                    {
                        sanskrit: "तुल्यनिन्दास्तुतिर्मौनी सन्तुष्टो येन केनचित्।",
                        translation: "A person who is equal in honor and dishonor, who is silent, satisfied with anything, without concern for residence, steady in mind, and engaged in devotional service, is very dear to Me.",
                        reference: "Bhagavad Gita 12.19"
                    }
                ]
            },
            angry: {
                title: "😠 Conquering Anger",
                subtitle: "Channel your energy into righteous action and peace",
                color: "linear-gradient(135deg, #F44336 0%, #d32f2f 100%)",
                shlokas: [
                    {
                        sanskrit: "क्रोधाद्भवति सम्मोहः सम्मोहात्स्मृतिविभ्रमः।",
                        translation: "From anger, delusion arises, and from delusion bewilderment of memory. When memory is bewildered, intelligence is lost, and when intelligence is lost, one falls down again into the material pool.",
                        reference: "Bhagavad Gita 2.63"
                    },
                    {
                        sanskrit: "धीरस्तत्र न मुह्यति। समदुःखसुखः स्वस्थः समलोष्टाश्मकाञ्चनः।",
                        translation: "The wise are not deluded by these. One who is undisturbed by happiness and distress and is steady in both, is certainly eligible for liberation.",
                        reference: "Bhagavad Gita 14.24"
                    },
                    {
                        sanskrit: "तितिक्षवः कारुणिकाः सुहृदः सर्वदेहिनाम्।",
                        translation: "The devotees of the Lord are so forbearing that they do not retaliate even when harassed by envious persons. They are merciful even to their enemies, and they are always kind to everyone.",
                        reference: "Bhagavad Gita 12.13-14"
                    },
                    {
                        sanskrit: "अमानित्वमदम्भित्वमहिंसा क्षान्तिरार्जवम्।",
                        translation: "Humility, pridelessness, non-violence, tolerance, simplicity, approaching a bona fide spiritual master, cleanliness, steadiness, self-control.",
                        reference: "Bhagavad Gita 13.8"
                    },
                    {
                        sanskrit: "अभयं सत्त्वसंशुद्धिर्ज्ञानयोगव्यवस्थितिः।",
                        translation: "Fearlessness, purification of one's existence, cultivation of spiritual knowledge, charity, self-control, performance of sacrifice, study of the Vedas, austerity, simplicity.",
                        reference: "Bhagavad Gita 16.1"
                    },
                    {
                        sanskrit: "क्षमा धृतिर्दमः शौचमद्रोहो नातिमानिता।",
                        translation: "Forgiveness, fortitude, cleanliness, envy-less-ness, and freedom from pride—these qualities belong to those endowed with divine nature, O son of Bharata.",
                        reference: "Bhagavad Gita 16.3"
                    }
                ]
            },
            fearful: {
                title: "😰 Overcoming Fear",
                subtitle: "Find courage through faith and divine protection",
                color: "linear-gradient(135deg, #9C27B0 0%, #7b1fa2 100%)",
                shlokas: [
                    {
                        sanskrit: "अभयं सत्त्वसंशुद्धिर्ज्ञानयोगव्यवस्थितिः।",
                        translation: "Fearlessness, purification of one's existence, cultivation of spiritual knowledge, charity, self-control, performance of sacrifice, study of the Vedas, austerity, simplicity—these are the godly qualities of men endowed with divine nature.",
                        reference: "Bhagavad Gita 16.1"
                    },
                    {
                        sanskrit: "न हि कल्याणकृत्कश्चिद्दुर्गतिं तात गच्छति।",
                        translation: "No one who does good work will ever come to a bad end, either here or in the world to come. My dear friend, a person who strives sincerely in spiritual life is never overcome by evil.",
                        reference: "Bhagavad Gita 6.40"
                    },
                    {
                        sanskrit: "यदा यदा हि धर्मस्य ग्लानिर्भवति भारत।",
                        translation: "Whenever and wherever there is a decline in dharma, O descendant of Bharata, and a predominant rise in adharma—at that time I descend Myself.",
                        reference: "Bhagavad Gita 4.7"
                    },
                    {
                        sanskrit: "सर्वधर्मान्परित्यज्य मामेकं शरणं व्रज।",
                        translation: "Abandon all varieties of religion and just surrender unto Me. I shall deliver you from all sinful reactions. Do not fear.",
                        reference: "Bhagavad Gita 18.66"
                    },
                    {
                        sanskrit: "न मे भक्तः प्रणश्यति।",
                        translation: "My devotee will never perish. I promise you this because you are very dear to Me.",
                        reference: "Bhagavad Gita 9.31"
                    }
                ]
            },
            confused: {
                title: "🤔 Clearing Confusion",
                subtitle: "Illuminate your path with divine wisdom and clarity",
                color: "linear-gradient(135deg, #FF9800 0%, #f57c00 100%)",
                shlokas: [
                    {
                        sanskrit: "यदा ते मोहकलिलं बुद्धिर्व्यतितरिष्यति।",
                        translation: "When your intelligence has passed out of the dense forest of delusion, you shall become indifferent to all that has been heard and all that is to be heard.",
                        reference: "Bhagavad Gita 2.52"
                    },
                    {
                        sanskrit: "तत्त्ववित्तु महाबाहो गुणकर्मविभागयोः।",
                        translation: "One who is in knowledge of the Absolute Truth, O mighty-armed, does not engage himself in the senses and sense gratification, knowing well the differences between work in devotion and work for fruitive results.",
                        reference: "Bhagavad Gita 3.28"
                    },
                    {
                        sanskrit: "उद्धरेदात्मनात्मानं नात्मानमवसादयेत्।",
                        translation: "One must deliver himself with the help of his mind, and not degrade himself. The mind is the friend of the conditioned soul, and his enemy as well.",
                        reference: "Bhagavad Gita 6.5"
                    },
                    {
                        sanskrit: "श्रेयान्स्वधर्मो विगुणः परधर्मात्स्वनुष्ठितात्।",
                        translation: "Better is one's own dharma, though imperfectly performed, than the dharma of another well performed. Better is death in the discharge of one's own dharma; the dharma of another is fraught with danger.",
                        reference: "Bhagavad Gita 3.35"
                    },
                    {
                        sanskrit: "कर्मण्येवाधिकारस्ते मा फलेषु कदाचन।",
                        translation: "You have a right to perform your prescribed duty, but not to the fruits of action. Never consider yourself the cause of the results of your activities, and never be attached to not doing your duty.",
                        reference: "Bhagavad Gita 2.47"
                    },
                    {
                        sanskrit: "बुद्धियुक्तो जहातीह उभे सुकृतदुष्कृते।",
                        translation: "A man engaged in devotional service rids himself of both good and bad actions even in this life. Therefore strive for yoga, which is the art of all work.",
                        reference: "Bhagavad Gita 2.50"
                    },
                    {
                        sanskrit: "ज्ञानं तेऽहं सविज्ञानमिदं वक्ष्याम्यशेषतः।",
                        translation: "I shall now declare unto you fully this knowledge, both phenomenal and transcendental. This being known, nothing further shall remain for you to know.",
                        reference: "Bhagavad Gita 7.2"
                    }
                ]
            },
            anxious: {
                title: "😟 Calming Anxiety",
                subtitle: "Find peace through surrender and trust in divine will",
                color: "linear-gradient(135deg, #E91E63 0%, #c2185b 100%)",
                shlokas: [
                    {
                        sanskrit: "योगस्थः कुरु कर्माणि सङ्गं त्यक्त्वा धनञ्जय।",
                        translation: "Therefore, O Arjuna, surrendering all your works unto Me, with full knowledge of Me, without desires for profit, with no claims to proprietorship, and free from lethargy, fight.",
                        reference: "Bhagavad Gita 3.30"
                    },
                    {
                        sanskrit: "मयि सर्वाणि कर्माणि संन्यस्याध्यात्मचेतसा।",
                        translation: "Therefore, O Arjuna, surrendering all your works unto Me, with mind intent on Me, and without desire for gain and free from egoism and lethargy, fight.",
                        reference: "Bhagavad Gita 3.30"
                    },
                    {
                        sanskrit: "तस्माद्सर्वेषु कालेषु मामनुस्मर युध्य च।",
                        translation: "Therefore, always think of Me, become My devotee, worship Me and offer your homage unto Me. Thus you will come to Me without fail. I promise you this because you are My very dear friend.",
                        reference: "Bhagavad Gita 8.7"
                    },
                    {
                        sanskrit: "समः शत्रौ च मित्रे च तथा मानापमानयोः।",
                        translation: "One who is equal to friends and enemies, who is equipoised in honor and dishonor, heat and cold, happiness and distress, fame and infamy, who is always free from contaminating association, always silent and satisfied with anything, who doesn't care for any residence, who is fixed in knowledge and who is engaged in devotional service—such a person is very dear to Me.",
                        reference: "Bhagavad Gita 12.18-19"
                    }
                ]
            },
            peaceful: {
                title: "🕊️ Deepening Peace",
                subtitle: "Cultivate inner tranquility through spiritual wisdom",
                color: "linear-gradient(135deg, #2196F3 0%, #1976d2 100%)",
                shlokas: [
                    {
                        sanskrit: "लभन्ते ब्रह्मनिर्वाणमृषयः क्षीणकल्मषाः।",
                        translation: "Those who are beyond the dualities that arise from doubts, whose minds are engaged within, who are always busy working for the welfare of all living beings, and who are free from all sins achieve liberation in the Supreme.",
                        reference: "Bhagavad Gita 5.25"
                    },
                    {
                        sanskrit: "शान्तिमाप्नोति न कामकामी।",
                        translation: "One who is not disturbed by the incessant flow of desires—that enter like rivers into the ocean, which is ever being filled but is always still—can alone achieve peace, and not the person who strives to satisfy such desires.",
                        reference: "Bhagavad Gita 2.70"
                    },
                    {
                        sanskrit: "युक्ताहारविहारस्य युक्तचेष्टस्य कर्मसु।",
                        translation: "He who is regulated in his habits of eating, sleeping, recreation and work can mitigate all material pains by practicing the yoga system.",
                        reference: "Bhagavad Gita 6.17"
                    },
                    {
                        sanskrit: "प्रशान्तमनसं ह्येनं योगिनं सुखमुत्तमम्।",
                        translation: "The yogi whose mind is fixed on Me verily attains the highest perfection of transcendental happiness. He is beyond the mode of passion, he realizes his qualitative identity with the Supreme, and thus he is freed from all reactions to past deeds.",
                        reference: "Bhagavad Gita 6.27"
                    },
                    {
                        sanskrit: "यस्त्वात्मरतिरेव स्यादात्मतृप्तश्च मानवः।",
                        translation: "But for one who takes pleasure in the self, whose human life is one of self-realization, and who is satisfied in the self only, there is no duty.",
                        reference: "Bhagavad Gita 3.17"
                    },
                    {
                        sanskrit: "ब्रह्मण्याधाय कर्माणि सङ्गं त्यक्त्वा करोति यः।",
                        translation: "One who performs his duty without attachment, surrendering the results unto the Supreme Lord, is unaffected by sinful action, as the lotus leaf is untouched by water.",
                        reference: "Bhagavad Gita 5.10"
                    }
                ]
            },
            motivated: {
                title: "🔥 Finding Motivation",
                subtitle: "Ignite your inner fire through righteous duty and purpose",
                color: "linear-gradient(135deg, #FF5722 0%, #d84315 100%)",
                shlokas: [
                    {
                        sanskrit: "उत्तिष्ठत जाग्रत प्राप्य वरान्निबोधत।",
                        translation: "Arise, awake, and stop not until the goal is reached. The path is like the sharp edge of a razor; it is difficult to cross and hard to tread.",
                        reference: "Inspired by Katha Upanishad (referenced in Gita teachings)"
                    },
                    {
                        sanskrit: "श्रेयान्स्वधर्मो विगुणः परधर्मात्स्वनुष्ठितात्।",
                        translation: "Better is one's own dharma, though imperfectly performed, than the dharma of another well performed. It is better to die in one's own dharma; the dharma of another is fraught with danger.",
                        reference: "Bhagavad Gita 3.35"
                    },
                    {
                        sanskrit: "कर्मण्येवाधिकारस्ते मा फलेषु कदाचन।",
                        translation: "You have a right to perform your prescribed duty, but not to the fruits of action. Never consider yourself the cause of the results of your activities, and never be attached to not doing your duty.",
                        reference: "Bhagavad Gita 2.47"
                    },
                    {
                        sanskrit: "यत्करोषि यदश्नासि यज्जुहोषि ददासि यत्।",
                        translation: "Whatever you do, whatever you eat, whatever you offer or give away, and whatever austerities you practice—do that, O son of Kunti, as an offering to God.",
                        reference: "Bhagavad Gita 9.27"
                    },
                    {
                        sanskrit: "योगः कर्मसु कौशलम्।",
                        translation: "Yoga is skill in action. Be steadfast in yoga, O Arjuna. Abandon attachment, be even-minded in success and failure, for evenness of mind is called yoga.",
                        reference: "Bhagavad Gita 2.50"
                    }
                ]
            }
        };

        function openModal(emotion) {
            const modal = document.getElementById('modal');
            const header = document.getElementById('modal-header');
            const title = document.getElementById('modal-title');
            const subtitle = document.getElementById('modal-subtitle');
            const container = document.getElementById('shlokas-container');
            
            const data = emotionData[emotion];
            
            // Set header content and color
            header.style.background = data.color;
            title.textContent = data.title;
            subtitle.textContent = data.subtitle;
            
            // Clear and populate shlokas
            container.innerHTML = '';
            data.shlokas.forEach((shloka, index) => {
                const shlokaCard = document.createElement('div');
                shlokaCard.className = 'shloka-card';
                shlokaCard.style.borderLeftColor = getColorFromGradient(data.color);
                
                shlokaCard.innerHTML = `
                    <div class="shloka-sanskrit">${shloka.sanskrit}</div>
                    <div class="shloka-translation">${shloka.translation}</div>
                    <div class="shloka-reference">${shloka.reference}</div>
                `;
                
                container.appendChild(shlokaCard);
            });
            
            modal.style.display = 'block';
            document.body.style.overflow = 'hidden';
        }

        function closeModal(event) {
            if (!event || event.target.id === 'modal' || event.target.className === 'close') {
                document.getElementById('modal').style.display = 'none';
                document.body.style.overflow = 'auto';
            }
        }

        function getColorFromGradient(gradient) {
            // Extract first color from gradient for border
            const match = gradient.match(/#[0-9A-Fa-f]{6}/);
            return match ? match[0] : '#333';
        }

        // Add some interactive sparkle effect on card hover
        document.addEventListener('DOMContentLoaded', function() {
            const cards = document.querySelectorAll('.emotion-card');
            
            cards.forEach(card => {
                card.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-10px) scale(1.02)';
                });
                
                card.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0) scale(1)';
                });
            });
        });

        // Close modal with Escape key
        document.addEventListener('keydown', function(event) {
            if (event.key === 'Escape') {
                closeModal(event);
            }
        });

        // Add floating animation to Om symbols
        function animateOmSymbols() {
            const oms = document.querySelectorAll('.floating-om');
            oms.forEach((om, index) => {
                om.style.animationDelay = `${index * -2}s`;
            });
        }

        animateOmSymbols();
    </script>
</body>
</html>
