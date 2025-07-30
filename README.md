<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Supreeth Rumalad - Portfolio</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- React & ReactDOM -->
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <!-- Babel for JSX transpilation -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&display=swap" rel="stylesheet">

    <style>
        /*
          This style block contains all the custom CSS from your original files.
          It defines the color theme, gradients, animations, and component styles.
        */
        @layer base {
          :root {
            /* Tech Theme - Violet & Black */
            --background: 220 30% 5%;
            --foreground: 270 100% 95%;
            --card: 220 25% 8%;
            --card-foreground: 270 100% 95%;
            --popover: 220 25% 8%;
            --popover-foreground: 270 100% 95%;
            --primary: 270 100% 65%;
            --primary-foreground: 220 30% 5%;
            --secondary: 220 20% 15%;
            --secondary-foreground: 270 100% 90%;
            --muted: 220 15% 12%;
            --muted-foreground: 270 20% 65%;
            --accent: 280 100% 70%;
            --accent-foreground: 220 30% 5%;
            --destructive: 0 84.2% 60.2%;
            --destructive-foreground: 270 100% 95%;
            --border: 220 20% 20%;
            --input: 220 20% 15%;
            --ring: 270 100% 65%;
            --radius: 0.5rem;
          }
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: hsl(var(--background));
            color: hsl(var(--foreground));
            overflow-x: hidden;
            position: relative;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 50% 50%, hsl(270 100% 65% / 0.1), transparent),
                        radial-gradient(circle at 20% 80%, hsl(280 100% 70% / 0.1), transparent),
                        radial-gradient(circle at 80% 20%, hsl(260 100% 60% / 0.1), transparent);
            pointer-events: none;
            z-index: -1;
            opacity: 0.6;
        }

        body::after {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: radial-gradient(circle at 1px 1px, hsla(270, 100%, 65%, 0.15) 1px, transparent 0);
            background-size: 20px 20px;
            pointer-events: none;
            z-index: -1;
            animation: grain 8s steps(10) infinite;
        }

        .tech-glow { box-shadow: 0 0 20px hsl(270 100% 65% / 0.5), 0 0 40px hsl(270 100% 65% / 0.3); }
        .accent-glow { box-shadow: 0 0 20px hsl(280 100% 70% / 0.5), 0 0 40px hsl(280 100% 70% / 0.3); }
        .text-glow { text-shadow: 0 0 10px hsl(270 100% 65% / 0.8); }
        .gradient-tech { background: linear-gradient(135deg, hsl(270 100% 20%), hsl(280 100% 40%), hsl(270 100% 65%)); }
        .gradient-flow { background: linear-gradient(90deg, hsl(270 100% 65%), hsl(280 100% 70%), hsl(290 100% 75%)); }
        .glass-card {
            background-color: hsla(var(--card), 0.5);
            backdrop-filter: blur(12px);
            border: 1px solid hsl(var(--border) / 0.5);
            border-radius: 0.5rem;
            box-shadow: 0 8px 32px 0 hsla(270, 100%, 65%, 0.1), inset 0 1px 0 0 hsla(270, 100%, 65%, 0.1);
        }
        .flow-line {
            background: linear-gradient(90deg, transparent, hsl(var(--primary)), transparent);
            animation: flow-line 2s ease-in-out infinite;
        }

        .animate-float { animation: float 6s ease-in-out infinite; }
        .animate-slide-in-left { animation: slide-in-left 0.8s ease-out; }
        .animate-slide-in-right { animation: slide-in-right 0.8s ease-out; }
        .animate-fade-in-up { animation: fade-in-up 0.8s ease-out; }

        @keyframes grain {
            0%, 100% { transform: translate(0, 0); } 10% { transform: translate(-5%, -10%); } 20% { transform: translate(-15%, 5%); } 30% { transform: translate(7%, -25%); } 40% { transform: translate(-5%, 25%); } 50% { transform: translate(-15%, 10%); } 60% { transform: translate(15%, 0%); } 70% { transform: translate(0%, 15%); } 80% { transform: translate(3%, 35%); } 90% { transform: translate(-10%, 10%); }
        }
        @keyframes float {
            0%, 100% { transform: translateY(0px); } 50% { transform: translateY(-20px); }
        }
        @keyframes slide-in-left {
            0% { transform: translateX(-100%); opacity: 0; } 100% { transform: translateX(0); opacity: 1; }
        }
        @keyframes slide-in-right {
            0% { transform: translateX(100%); opacity: 0; } 100% { transform: translateX(0); opacity: 1; }
        }
        @keyframes fade-in-up {
            0% { transform: translateY(30px); opacity: 0; } 100% { transform: translateY(0); opacity: 1; }
        }
        @keyframes flow-line {
            0% { transform: translateX(-100%); } 100% { transform: translateX(100%); }
        }
    </style>
</head>
<body>
    <div id="root"></div>
    <div id="toast-container" class="fixed bottom-5 right-5 z-[100]"></div>

    {% raw %}
    <script type="text/babel">
        // Helper to get HSL colors for Tailwind
        const withOpacity = (variableName) => ({ opacityValue }) => {
            if (opacityValue !== undefined) {
                return `hsla(var(${variableName}), ${opacityValue})`;
            }
            return `hsl(var(${variableName}))`;
        };

        // Configure Tailwind to use custom theme colors
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        border: withOpacity('--border'),
                        input: withOpacity('--input'),
                        ring: withOpacity('--ring'),
                        background: withOpacity('--background'),
                        foreground: withOpacity('--foreground'),
                        primary: {
                            DEFAULT: withOpacity('--primary'),
                            foreground: withOpacity('--primary-foreground'),
                        },
                        secondary: {
                            DEFAULT: withOpacity('--secondary'),
                            foreground: withOpacity('--secondary-foreground'),
                        },
                        destructive: {
                            DEFAULT: withOpacity('--destructive'),
                            foreground: withOpacity('--destructive-foreground'),
                        },
                        muted: {
                            DEFAULT: withOpacity('--muted'),
                            foreground: withOpacity('--muted-foreground'),
                        },
                        accent: {
                            DEFAULT: withOpacity('--accent'),
                            foreground: withOpacity('--accent-foreground'),
                        },
                        popover: {
                            DEFAULT: withOpacity('--popover'),
                            foreground: withOpacity('--popover-foreground'),
                        },
                        card: {
                            DEFAULT: withOpacity('--card'),
                            foreground: withOpacity('--card-foreground'),
                        },
                    },
                    borderRadius: {
                        lg: `var(--radius)`,
                        md: `calc(var(--radius) - 2px)`,
                        sm: 'calc(var(--radius) - 4px)',
                    },
                },
            },
        };

        const { useState, useEffect, useRef } = React;

        // --- Icon Components (Replacing lucide-react) ---
        const Icon = ({ children, className }) => <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}>{children}</svg>;
        const Mail = ({ className }) => <Icon className={className}><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></Icon>;
        const Phone = ({ className }) => <Icon className={className}><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path></Icon>;
        const MapPin = ({ className }) => <Icon className={className}><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path><circle cx="12" cy="10" r="3"></circle></Icon>;
        const Send = ({ className }) => <Icon className={className}><line x1="22" y1="2" x2="11" y2="13"></line><polygon points="22 2 15 22 11 13 2 9 22 2"></polygon></Icon>;
        const Github = ({ className }) => <Icon className={className}><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></Icon>;
        const Linkedin = ({ className }) => <Icon className={className}><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></Icon>;
        const Instagram = ({ className }) => <Icon className={className}><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></Icon>;
        const GraduationCap = ({ className }) => <Icon className={className}><path d="M22 10v6M2 10l10-5 10 5-10 5z"></path><path d="M6 12v5c3 3 12 3 15 0v-5"></path></Icon>;
        const Calendar = ({ className }) => <Icon className={className}><rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect><line x1="16" y1="2" x2="16" y2="6"></line><line x1="8" y1="2" x2="8" y2="6"></line><line x1="3" y1="10" x2="21" y2="10"></line></Icon>;
        const Award = ({ className }) => <Icon className={className}><circle cx="12" cy="8" r="7"></circle><polyline points="8.21 13.89 7 22 12 17 17 22 15.79 13.88"></polyline></Icon>;
        const Trophy = ({ className }) => <Icon className={className}><path d="M6 9H4.5a2.5 2.5 0 0 1 0-5H6"></path><path d="M18 9h1.5a2.5 2.5 0 0 0 0-5H18"></path><path d="M4 22h16"></path><path d="M10 14.66V17c0 .55-.47.98-.97 1.21C7.85 18.75 7 20.24 7 22"></path><path d="M14 14.66V17c0 .55.47.98.97 1.21C16.15 18.75 17 20.24 17 22"></path><path d="M18 2H6v7a6 6 0 0 0 12 0V2z"></path></Icon>;
        const Target = ({ className }) => <Icon className={className}><circle cx="12" cy="12" r="10"></circle><circle cx="12" cy="12" r="6"></circle><circle cx="12" cy="12" r="2"></circle></Icon>;
        const Heart = ({ className }) => <Icon className={className}><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path></Icon>;
        const Zap = ({ className }) => <Icon className={className}><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon></Icon>;
        const Menu = ({ className }) => <Icon className={className}><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></Icon>;
        const X = ({ className }) => <Icon className={className}><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></Icon>;
        const ExternalLink = ({ className }) => <Icon className={className}><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></Icon>;
        const Brain = ({ className }) => <Icon className={className}><path d="M9.5 2A2.5 2.5 0 0 1 12 4.5v15a2.5 2.5 0 0 1-4.94.44c-.4-1.56.22-3.33 1.44-4.44M14.5 2A2.5 2.5 0 0 0 12 4.5v15a2.5 2.5 0 0 0 4.94.44c.4-1.56-.22-3.33-1.44-4.44M5 11.5A2.5 2.5 0 0 1 7.5 9h9a2.5 2.5 0 0 1 2.5 2.5v0A2.5 2.5 0 0 1 16.5 14h-9A2.5 2.5 0 0 1 5 11.5z"></path></Icon>;
        const Globe = ({ className }) => <Icon className={className}><circle cx="12" cy="12" r="10"></circle><line x1="2" y1="12" x2="22" y2="12"></line><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"></path></Icon>;
        const MessageSquare = ({ className }) => <Icon className={className}><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path></Icon>;
        const Code = ({ className }) => <Icon className={className}><polyline points="16 18 22 12 16 6"></polyline><polyline points="8 6 2 12 8 18"></polyline></Icon>;
        const Database = ({ className }) => <Icon className={className}><ellipse cx="12" cy="5" rx="9" ry="3"></ellipse><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"></path><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"></path></Icon>;
        const Cloud = ({ className }) => <Icon className={className}><path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"></path></Icon>;
        const Shield = ({ className }) => <Icon className={className}><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path></Icon>;

        // --- UI Components (Replacing custom library components) ---
        const Button = ({ children, className, variant, size, ...props }) => {
            const baseClasses = "inline-flex items-center justify-center rounded-md text-sm font-medium transition-colors focus:outline-none focus:ring-2 focus:ring-ring focus:ring-offset-2 disabled:opacity-50 disabled:pointer-events-none";
            const sizeClasses = {
                default: "h-10 py-2 px-4",
                sm: "h-9 px-3 rounded-md",
                lg: "h-11 px-8 rounded-md",
            };
            const variantClasses = {
                default: "bg-primary text-primary-foreground hover:bg-primary/90",
                outline: "border border-input hover:bg-accent hover:text-accent-foreground",
                ghost: "hover:bg-accent hover:text-accent-foreground",
            };
            const finalClassName = `${baseClasses} ${sizeClasses[size] || sizeClasses.default} ${variantClasses[variant] || variantClasses.default} ${className}`;
            return <button className={finalClassName} {...props}>{children}</button>;
        };
        const Input = ({ className, ...props }) => {
            const baseClasses = "flex h-10 w-full rounded-md border border-input bg-transparent px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50";
            return <input className={`${baseClasses} ${className}`} {...props} />;
        };
        const Textarea = ({ className, ...props }) => {
            const baseClasses = "flex min-h-[80px] w-full rounded-md border border-input bg-transparent px-3 py-2 text-sm ring-offset-background placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50";
            return <textarea className={`${baseClasses} ${className}`} {...props} />;
        };

        // --- Toast Notification System ---
        const Toast = ({ message, id, onDismiss }) => {
            useEffect(() => {
                const timer = setTimeout(() => {
                    onDismiss(id);
                }, 3000);
                return () => clearTimeout(timer);
            }, [id, onDismiss]);

            return (
                <div className="bg-green-500/20 border border-green-500 text-green-300 px-4 py-3 rounded-lg relative mb-2 shadow-lg animate-fade-in-up" role="alert">
                    <strong className="font-bold">Success!</strong>
                    <span className="block sm:inline ml-2">{message}</span>
                </div>
            );
        };

        const ToastContainer = ({ toasts, dismissToast }) => {
            return ReactDOM.createPortal(
                <div className="fixed bottom-5 right-5 z-[100]">
                    {toasts.map((toast) => (
                        <Toast key={toast.id} {...toast} onDismiss={dismissToast} />
                    ))}
                </div>,
                document.getElementById('toast-container')
            );
        };
        
        // --- ScrollTrack Component ---
        const ScrollTrack = () => {
            const [scrollY, setScrollY] = useState(0);
            const [indicatorPosition, setIndicatorPosition] = useState(0);
            const pathRef = useRef(null);

            useEffect(() => {
                const handleScroll = () => {
                    const scrolled = window.scrollY;
                    const maxScroll = document.documentElement.scrollHeight - window.innerHeight;
                    const scrollPercentage = maxScroll > 0 ? scrolled / maxScroll : 0;
                    
                    setScrollY(scrolled);
                    
                    if (pathRef.current) {
                        const pathLength = pathRef.current.getTotalLength();
                        setIndicatorPosition(pathLength * scrollPercentage);
                    }
                };

                window.addEventListener('scroll', handleScroll);
                // Call handler once to set initial position
                handleScroll();
                return () => window.removeEventListener('scroll', handleScroll);
            }, []);

            const trackPath = "M 50 20 C 50 20, 50 100, 50 180";

            return (
                <div className="fixed top-0 right-6 w-24 h-full pointer-events-none z-50 opacity-60 hidden lg:block">
                    <svg className="w-full h-full" viewBox="0 0 100 200" preserveAspectRatio="xMidYMin meet">
                        <defs>
                            <linearGradient id="trackGradient" x1="0%" y1="0%" x2="0%" y2="100%">
                                <stop offset="0%" stopColor="hsl(var(--primary))" stopOpacity="0.3" />
                                <stop offset="50%" stopColor="hsl(var(--accent))" stopOpacity="0.2" />
                                <stop offset="100%" stopColor="hsl(var(--primary))" stopOpacity="0.3" />
                            </linearGradient>
                        </defs>
                        
                        <path d={trackPath} fill="none" stroke="url(#trackGradient)" strokeWidth="8" className="drop-shadow-lg" />
                        <path d={trackPath} fill="none" stroke="hsl(var(--muted-foreground))" strokeWidth="2" strokeDasharray="4 4" className="opacity-50" />
                        
                        <path
                            ref={pathRef}
                            d={trackPath}
                            fill="none"
                            stroke="hsl(var(--primary))"
                            strokeWidth="4"
                            strokeDasharray={pathRef.current ? pathRef.current.getTotalLength() : 0}
                            strokeDashoffset={pathRef.current ? pathRef.current.getTotalLength() - indicatorPosition : 0}
                            style={{
                                transition: 'stroke-dashoffset 0.1s ease-out',
                                filter: 'drop-shadow(0 0 8px hsl(var(--primary)))'
                            }}
                        />
                    </svg>

                    <div className="absolute top-4 left-1/2 transform -translate-x-1/2 text-xs text-primary font-bold bg-background/80 px-2 py-1 rounded">
                        {Math.floor((indicatorPosition / (pathRef.current ? pathRef.current.getTotalLength() : 1)) * 100)}%
                    </div>
                </div>
            );
        };

        // --- ContactSection Component ---
        const ContactSection = ({ addToast }) => {
            const [formData, setFormData] = useState({ name: '', email: '', message: '' });

            const handleSubmit = (e) => {
                e.preventDefault();
                addToast("Message sent successfully! I'll get back to you soon.");
                setFormData({ name: '', email: '', message: '' });
            };

            const handleChange = (e) => {
                setFormData({ ...formData, [e.target.name]: e.target.value });
            };

            const contactInfo = [
                { icon: Phone, label: "Phone", value: "9454987101", href: "tel:+919454987101" },
                { icon: Mail, label: "Email", value: "supreeth8055@gmail.com", href: "mailto:supreeth8055@gmail.com" },
                { icon: MapPin, label: "Location", value: "Bengaluru, Karnataka, India", href: "#" }
            ];

            return (
                <section id="contact" className="py-20 relative">
                    <div className="container mx-auto px-6">
                        <div className="text-center mb-16">
                            <h2 className="text-4xl font-bold mb-4"><span className="text-glow">Connect & Collaborate</span></h2>
                            <p className="text-xl text-muted-foreground max-w-2xl mx-auto">Ready to build something amazing together? Let's connect and create innovative solutions.</p>
                            <div className="w-24 h-1 bg-gradient-flow mx-auto mt-6 rounded-full"></div>
                        </div>

                        <div className="grid lg:grid-cols-2 gap-12 max-w-6xl mx-auto">
                            <div className="space-y-8">
                                <div>
                                    <h3 className="text-2xl font-bold text-foreground mb-6">Get In Touch</h3>
                                    <p className="text-muted-foreground text-lg leading-relaxed mb-8">Whether you're looking for a collaborator on your next AI project, need help with data analytics, or just want to discuss the latest in technology, I'm always excited to connect with fellow innovators.</p>
                                </div>
                                <div className="space-y-6">
                                    {contactInfo.map((info, index) => {
                                        const IconComponent = info.icon;
                                        return (
                                            <div key={info.label} className="flex items-center space-x-4 p-4 glass-card hover:tech-glow transition-all duration-300 animate-fade-in-up" style={{ animationDelay: `${index * 0.1}s` }}>
                                                <div className="p-3 rounded-lg bg-primary/10"><IconComponent className="w-6 h-6 text-primary" /></div>
                                                <div>
                                                    <p className="text-sm text-muted-foreground">{info.label}</p>
                                                    <a href={info.href} className="text-foreground font-medium hover:text-primary transition-colors">{info.value}</a>
                                                </div>
                                            </div>
                                        );
                                    })}
                                </div>
                                <div className="pt-8">
                                    <h4 className="text-lg font-semibold text-foreground mb-4">Connect on Social</h4>
                                    <div className="flex space-x-4">
                                        <a href="https://github.com/Supreeth44" target="_blank" rel="noopener noreferrer" className="p-3 glass-card hover:tech-glow transition-all duration-300 group"><Github className="w-6 h-6 text-muted-foreground group-hover:text-primary transition-colors" /></a>
                                        <a href="https://www.linkedin.com/in/supreeth-rumalad-3b65a235a/" target="_blank" rel="noopener noreferrer" className="p-3 glass-card hover:accent-glow transition-all duration-300 group"><Linkedin className="w-6 h-6 text-muted-foreground group-hover:text-accent transition-colors" /></a>
                                        <a href="https://www.instagram.com/supreeth_r/" target="_blank" rel="noopener noreferrer" className="p-3 glass-card hover:accent-glow transition-all duration-300 group"><Instagram className="w-6 h-6 text-muted-foreground group-hover:text-accent transition-colors" /></a>
                                    </div>
                                </div>
                            </div>
                            <div className="glass-card p-8">
                                <h3 className="text-2xl font-bold text-foreground mb-6">Send a Message</h3>
                                <form onSubmit={handleSubmit} className="space-y-6">
                                    <div>
                                        <label htmlFor="name" className="block text-sm font-medium text-foreground mb-2">Name</label>
                                        <Input id="name" name="name" type="text" value={formData.name} onChange={handleChange} required className="bg-secondary/50 border-border/50 focus:border-primary focus:ring-primary" placeholder="Your name" />
                                    </div>
                                    <div>
                                        <label htmlFor="email" className="block text-sm font-medium text-foreground mb-2">Email</label>
                                        <Input id="email" name="email" type="email" value={formData.email} onChange={handleChange} required className="bg-secondary/50 border-border/50 focus:border-primary focus:ring-primary" placeholder="your.email@example.com" />
                                    </div>
                                    <div>
                                        <label htmlFor="message" className="block text-sm font-medium text-foreground mb-2">Message</label>
                                        <Textarea id="message" name="message" value={formData.message} onChange={handleChange} required rows={5} className="bg-secondary/50 border-border/50 focus:border-primary focus:ring-primary resize-none" placeholder="Tell me about your project or just say hello..." />
                                    </div>
                                    <Button type="submit" size="lg" className="w-full tech-glow hover:accent-glow transition-all duration-300"><Send className="w-4 h-4 mr-2" />Send Message</Button>
                                </form>
                            </div>
                        </div>
                        <div className="mt-16 text-center">
                            <div className="glass-card p-8 max-w-2xl mx-auto">
                                <h3 className="text-2xl font-bold text-foreground mb-4">Download My Resume</h3>
                                <p className="text-muted-foreground mb-6">Get a detailed overview of my experience, skills, and achievements in a downloadable format.</p>
                                <Button size="lg" className="tech-glow hover:accent-glow" onClick={() => addToast("Resume download will be available soon!")}><Mail className="w-4 h-4 mr-2" />Download Resume</Button>
                            </div>
                        </div>
                    </div>
                </section>
            );
        };

        // --- EducationSection Component ---
        const EducationSection = () => {
            const education = [
                { degree: "Bachelor of Engineering - Computer Science & Engineering", institution: "Sapthagiri College of Engineering", university: "Visvesvaraya Technological University (VTU)", period: "December 2022 - June 2026", location: "Bengaluru, Karnataka", status: "Currently Pursuing", type: "Bachelor's Degree" },
                { degree: "PUC, Computer Science", institution: "Vidya Mandir IND PU College", period: "June 2020 - April 2022", location: "Bengaluru, Karnataka", status: "Completed", type: "Pre-University" },
                { degree: "10th Standard", institution: "Sri Vidya Mandir", period: "2017 - 2020", location: "Bengaluru, Karnataka", status: "Completed", type: "Secondary Education" }
            ];
            const certifications = ["TATA Technologies Certification", "Deloitte Australia - Data Analytics Job Simulation", "AWS Academy Graduate"];
            const languages = [ { name: "English", level: "Fluent", percentage: 95 }, { name: "Hindi", level: "Native", percentage: 95 }, { name: "German", level: "A2", percentage: 20 } ];

            const EducationCard = ({ edu, index }) => (
                <div className="glass-card p-6 hover:tech-glow transition-all duration-300 animate-fade-in-up" style={{ animationDelay: `${index * 0.2}s` }}>
                    <div className="flex items-start justify-between mb-4">
                        <div className="flex items-center">
                            <div className="p-3 rounded-lg bg-primary/10 mr-4"><GraduationCap className="w-8 h-8 text-primary" /></div>
                            <div><span className="px-3 py-1 text-xs font-medium bg-accent/20 text-accent rounded-full">{edu.type}</span></div>
                        </div>
                        <span className={`px-3 py-1 text-xs font-medium rounded-full ${edu.status === 'Currently Pursuing' ? 'bg-primary/20 text-primary' : 'bg-green-500/20 text-green-400'}`}>{edu.status}</span>
                    </div>
                    <h3 className="text-xl font-bold text-foreground mb-2">{edu.degree}</h3>
                    <p className="text-lg text-accent font-medium mb-2">{edu.institution}</p>
                    {edu.university && <p className="text-muted-foreground mb-4">{edu.university}</p>}
                    <div className="flex flex-wrap gap-4 text-sm text-muted-foreground">
                        <div className="flex items-center"><Calendar className="w-4 h-4 mr-2" />{edu.period}</div>
                        <div className="flex items-center"><MapPin className="w-4 h-4 mr-2" />{edu.location}</div>
                    </div>
                </div>
            );

            return (
                <section id="education" className="py-20 relative">
                    <div className="container mx-auto px-6">
                        <div className="text-center mb-16">
                            <h2 className="text-4xl font-bold mb-4"><span className="text-glow">Education</span></h2>
                            <p className="text-xl text-muted-foreground max-w-2xl mx-auto">My educational journey through the technology landscape, building the foundation for innovation.</p>
                            <div className="w-24 h-1 bg-gradient-flow mx-auto mt-6 rounded-full"></div>
                        </div>

                        <div className="mb-16">
                            <h3 className="text-2xl font-bold text-center mb-8 text-primary">Education</h3>
                            <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                                {education.map((edu, index) => <EducationCard key={`${edu.institution}-${edu.period}`} edu={edu} index={index} />)}
                            </div>
                        </div>

                        <div className="mb-16">
                            <h3 className="text-2xl font-bold text-center mb-8 text-accent">Certifications & Achievements</h3>
                            <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                                {certifications.map((cert, index) => (
                                    <div key={cert} className="glass-card p-6 text-center hover:accent-glow transition-all duration-300 animate-fade-in-up" style={{ animationDelay: `${index * 0.1}s` }}>
                                        <Award className="w-12 h-12 text-accent mx-auto mb-4" />
                                        <h4 className="font-semibold text-foreground">{cert}</h4>
                                    </div>
                                ))}
                            </div>
                        </div>
                    </div>
                </section>
            );
        };

        // --- ExperienceSection Component ---
        const ExperienceSection = () => {
             const experiences = [
                { title: "Data Analytics & AI Strategy Virtual Intern", company: "Tata Consultancy Services (TCS)", period: "January 2025", location: "Virtual", type: "Internship", achievements: ["Conducted statistical EDA analysis to assess data quality and identify risk indicators for predictive modeling", "Designed an AI-driven collections strategy and a no-code predictive model to assess customer delinquency risk"] },
                { title: "Data Visualization Virtual Intern", company: "Tata Consultancy Services (TCS)", period: "February 2025", location: "Virtual", type: "Internship", achievements: ["Created compelling data visualizations in Tableau to support executive decision-making", "Prepared strategic questions for senior client leadership based on data analysis"] },
                { title: "Data Analytics & Forensic Technology Virtual Intern", company: "Deloitte Australia", period: "July 2025", location: "Virtual", type: "Internship", achievements: ["Analyzed and classified data using Excel to derive business insights and support forensic investigations", "Developed a dynamic data dashboard in Tableau for clear presentation of findings"] },
                { title: "Core Team Member", company: "Google Developer Student Club (GDSC)", period: "2024 - Present", location: "Sapthagiri College of Engineering", type: "Leadership", achievements: ["Organized and led technical events and workshops on various Google technologies", "Fostered a community of student developers and promoted peer-to-peer learning", "Actively participated in Hackathons and collaborative tech projects"] }
            ];
            
            const ExperienceCard = ({ exp, index }) => (
                <div className="relative animate-fade-in-up" style={{ animationDelay: `${index * 0.2}s` }}>
                    <div className="absolute left-6 top-16 bottom-0 w-px bg-gradient-flow"></div>
                    <div className="absolute left-4 top-6 w-4 h-4 rounded-full bg-primary tech-glow"></div>
                    <div className="ml-16 glass-card p-6 hover:tech-glow transition-all duration-300 group">
                        <div className="flex flex-wrap items-center gap-2 mb-4">
                            <span className="px-3 py-1 text-xs font-medium bg-primary/20 text-primary rounded-full">{exp.type}</span>
                            <div className="flex items-center text-sm text-muted-foreground"><Calendar className="w-4 h-4 mr-1" />{exp.period}</div>
                            <div className="flex items-center text-sm text-muted-foreground"><MapPin className="w-4 h-4 mr-1" />{exp.location}</div>
                        </div>
                        <h3 className="text-xl font-bold text-foreground mb-2 group-hover:text-primary transition-colors">{exp.title}</h3>
                        <p className="text-lg text-accent font-medium mb-4">{exp.company}</p>
                        <div className="space-y-3">
                            {exp.achievements.map((achievement, i) => (
                                <div key={i} className="flex items-start">
                                    <Target className="w-4 h-4 text-primary mr-3 mt-1 flex-shrink-0" />
                                    <p className="text-muted-foreground">{achievement}</p>
                                </div>
                            ))}
                        </div>
                    </div>
                </div>
            );

            return (
                <section id="experience" className="py-20 relative">
                    <div className="container mx-auto px-6">
                        <div className="text-center mb-16">
                            <h2 className="text-4xl font-bold mb-4"><span className="text-glow">Experience</span></h2>
                            <p className="text-xl text-muted-foreground max-w-2xl mx-auto">My journey through the data science and technology landscape, tackling challenges and building solutions.</p>
                            <div className="w-24 h-1 bg-gradient-flow mx-auto mt-6 rounded-full"></div>
                        </div>
                        <div className="max-w-4xl mx-auto">
                            <div className="space-y-8">
                                {experiences.map((exp, index) => <ExperienceCard key={`${exp.company}-${exp.period}`} exp={exp} index={index} />)}
                            </div>
                        </div>
                    </div>
                </section>
            );
        };

        // --- FooterSection Component ---
        const FooterSection = () => {
            const currentYear = new Date().getFullYear();
            const scrollToTop = () => window.scrollTo({ top: 0, behavior: 'smooth' });

            return (
                <footer className="relative py-16 mt-20">
                    <div className="absolute inset-0 bg-gradient-flow/10"></div>
                    <div className="absolute inset-0 bg-gradient-to-t from-background via-background/50 to-transparent"></div>
                    <div className="container mx-auto px-6 relative z-10">
                        <div className="grid md:grid-cols-3 gap-12 mb-12">
                            <div className="space-y-6">
                                <div className="flex items-center space-x-3">
                                    <div className="p-2 rounded-lg bg-primary/10 tech-glow"><Zap className="w-6 h-6 text-primary" /></div>
                                    <span className="text-2xl font-bold text-glow">Supreeth Rumalad</span>
                                </div>
                                <p className="text-muted-foreground leading-relaxed">CSE Student & Aspiring Software Engineer passionate about AI, ML, and building high-performance applications.</p>
                                <div className="flex space-x-4">
                                  <a href="https://github.com/Supreeth44" target="_blank" rel="noopener noreferrer" className="p-3 glass-card hover:tech-glow transition-all duration-300 group"><Github className="w-5 h-5 text-muted-foreground group-hover:text-primary transition-colors" /></a>
                                  <a href="https://www.linkedin.com/in/supreeth-rumalad-3b65a235a/" target="_blank" rel="noopener noreferrer" className="p-3 glass-card hover:accent-glow transition-all duration-300 group"><Linkedin className="w-5 h-5 text-muted-foreground group-hover:text-accent transition-colors" /></a>
                                  <a href="mailto:supreeth8055@gmail.com" className="p-3 glass-card hover:tech-glow transition-all duration-300 group"><Mail className="w-5 h-5 text-muted-foreground group-hover:text-primary transition-colors" /></a>
                                </div>
                            </div>
                            <div>
                                <h3 className="text-lg font-semibold text-foreground mb-6">Quick Navigation</h3>
                                <div className="space-y-3">
                                    {['Home', 'Skills', 'Experience', 'Projects', 'Education', 'Contact'].map(name => (
                                        <button key={name} onClick={() => document.getElementById(name.toLowerCase())?.scrollIntoView({ behavior: 'smooth' })} className="block text-muted-foreground hover:text-primary transition-colors">{name}</button>
                                    ))}
                                </div>
                            </div>
                            <div>
                                <h3 className="text-lg font-semibold text-foreground mb-6">Get In Touch</h3>
                                <div className="space-y-4">
                                    <div><p className="text-sm text-muted-foreground">Email</p><a href="mailto:supreeth8055@gmail.com" className="text-foreground hover:text-primary transition-colors">supreeth8055@gmail.com</a></div>
                                    <div><p className="text-sm text-muted-foreground">Phone</p><a href="tel:+919454987101" className="text-foreground hover:text-primary transition-colors">+91 9454987101</a></div>
                                    <div><p className="text-sm text-muted-foreground">Location</p><p className="text-foreground">Bengaluru, Karnataka, India</p></div>
                                </div>
                            </div>
                        </div>
                        <div className="w-full h-px bg-gradient-flow mb-8"></div>
                        <div className="flex flex-col md:flex-row justify-between items-center space-y-4 md:space-y-0">
                            <div className="flex items-center space-x-2 text-muted-foreground">
                                <span>© {currentYear} Supreeth Rumalad. Built with</span>
                                <Heart className="w-4 h-4 text-red-400 animate-pulse" />
                                <span>and lots of caffeine ☕</span>
                            </div>
                            <button onClick={scrollToTop} className="flex items-center space-x-2 text-muted-foreground hover:text-primary transition-colors group">
                                <span>Back to top</span>
                                <div className="p-1 rounded border border-border group-hover:border-primary transition-colors"><Zap className="w-4 h-4 transform -rotate-90" /></div>
                            </button>
                        </div>
                    </div>
                </footer>
            );
        };

        // --- HeroSection Component ---
        const HeroSection = () => {
            const [isVisible, setIsVisible] = useState(false);
            useEffect(() => { setIsVisible(true); }, []);
            const scrollToSection = (sectionId) => document.getElementById(sectionId)?.scrollIntoView({ behavior: 'smooth' });

            return (
                <section className="min-h-[80vh] flex items-center justify-center relative overflow-hidden py-12">
                    <div className="absolute inset-0 pointer-events-none">
                        <div className="absolute top-1/4 left-1/4 w-48 h-48 rounded-full bg-primary/10 blur-3xl animate-float"></div>
                        <div className="absolute bottom-1/4 right-1/4 w-64 h-64 rounded-full bg-accent/10 blur-3xl animate-float" style={{ animationDelay: '2s' }}></div>
                    </div>
                    <div className="container mx-auto px-6 z-10">
                        <div className="grid lg:grid-cols-3 gap-8 items-center">
                            <div className={`lg:col-span-2 space-y-6 ${isVisible ? 'animate-slide-in-left' : 'opacity-0'}`}>
                                <div>
                                    <h2 className="text-base font-medium text-accent mb-2">Welcome to innovation</h2>
                                    <h1 className="text-4xl lg:text-5xl font-bold mb-3">
                                        <span className="text-glow bg-gradient-to-r from-primary via-accent to-primary bg-clip-text text-transparent">Supreeth</span><br />
                                        <span className="text-foreground">Rumalad</span>
                                    </h1>
                                    <p className="text-lg text-muted-foreground mb-4">CSE Student at Sapthagiri College of Engineering (VTU)</p>
                                    <p className="text-base text-foreground/80 leading-relaxed">Aspiring Software Engineer with a passion for AI, ML, and high-performance applications. Building innovative solutions with cutting-edge technology.</p>
                                </div>
                                <div className="flex flex-wrap gap-3">
                                    <Button size="default" className="tech-glow hover:accent-glow transition-all duration-300" onClick={() => scrollToSection('projects')}>View Projects</Button>
                                    <Button variant="outline" size="default" className="border-primary/50 hover:bg-primary/10 hover:tech-glow" onClick={() => scrollToSection('contact')}><Mail className="w-4 h-4 mr-2" />Contact Me</Button>
                                </div>
                                <div className="flex gap-4">
                                    <a href="https://github.com/Supreeth44" target="_blank" rel="noopener noreferrer" className="text-muted-foreground hover:text-primary transition-colors hover:tech-glow p-2 rounded-lg group"><Github className="w-5 h-5 group-hover:scale-110 transition-transform" /></a>
                                    <a href="https://www.linkedin.com/in/supreeth-rumalad-3b65a235a/" target="_blank" rel="noopener noreferrer" className="text-muted-foreground hover:text-accent transition-colors hover:accent-glow p-2 rounded-lg group"><Linkedin className="w-5 h-5 group-hover:scale-110 transition-transform" /></a>
                                    <a href="mailto:supreeth8055@gmail.com" className="text-muted-foreground hover:text-primary transition-colors hover:tech-glow p-2 rounded-lg group"><Mail className="w-5 h-5 group-hover:scale-110 transition-transform" /></a>
                                </div>
                            </div>
                            <div className={`flex flex-col items-center space-y-4 ${isVisible ? 'animate-slide-in-right' : 'opacity-0'}`}>
                                <div className="relative group cursor-pointer" onClick={() => scrollToSection('experience')}>
                                    <img src="https://placehold.co/144x144/7c3aed/ffffff?text=SR" alt="Supreeth Rumalad" className="w-32 h-32 lg:w-36 lg:h-36 object-cover rounded-full border-4 border-primary/50 tech-glow group-hover:scale-105 transition-all duration-300" />
                                    <div className="absolute inset-0 rounded-full bg-gradient-radial from-primary/20 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                                </div>
                                <div className="flex gap-4">
                                    <div className="glass-card p-3 hover:tech-glow transition-all cursor-pointer group"><div className="text-lg font-bold text-primary group-hover:scale-110 transition-transform">3+</div><div className="text-xs text-muted-foreground">Years</div></div>
                                    <div className="glass-card p-3 hover:accent-glow transition-all cursor-pointer group"><div className="text-lg font-bold text-accent group-hover:scale-110 transition-transform">10+</div><div className="text-xs text-muted-foreground">Projects</div></div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div className="absolute bottom-4 left-1/2 transform -translate-x-1/2 animate-bounce">
                        <div className="w-5 h-8 border-2 border-primary/50 rounded-full flex justify-center"><div className="w-1 h-2 bg-primary rounded-full mt-1 animate-pulse"></div></div>
                    </div>
                </section>
            );
        };
        
        // --- Navigation Component ---
        const Navigation = () => {
            const [isScrolled, setIsScrolled] = useState(false);
            const [isMobileMenuOpen, setIsMobileMenuOpen] = useState(false);

            useEffect(() => {
                const handleScroll = () => setIsScrolled(window.scrollY > 50);
                window.addEventListener('scroll', handleScroll);
                return () => window.removeEventListener('scroll', handleScroll);
            }, []);

            const navItems = [{ name: 'Home', href: '#home' }, { name: 'Skills', href: '#skills' }, { name: 'Experience', href: '#experience' }, { name: 'Projects', href: '#projects' }, { name: 'Contact', href: '#contact' }];
            const scrollToSection = (href) => {
                document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' });
                setIsMobileMenuOpen(false);
            };

            return (
                <nav className={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 ${isScrolled ? 'bg-background/80 backdrop-blur-md border-b border-border/50' : 'bg-transparent'}`}>
                    <div className="container mx-auto px-6">
                        <div className="flex items-center justify-between h-16">
                            <div className="flex items-center space-x-3">
                                <div className="p-2 rounded-lg bg-primary/10 tech-glow"><Zap className="w-6 h-6 text-primary" /></div>
                                <span className="text-xl font-bold text-glow">Supreeth</span>
                            </div>
                            <div className="hidden md:flex items-center space-x-8">
                                {navItems.map((item) => (
                                    <button key={item.name} onClick={() => scrollToSection(item.href)} className="text-muted-foreground hover:text-primary transition-colors relative group">
                                        {item.name}
                                        <span className="absolute bottom-0 left-0 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"></span>
                                    </button>
                                ))}
                            </div>
                            <Button variant="ghost" size="sm" className="md:hidden" onClick={() => setIsMobileMenuOpen(!isMobileMenuOpen)}>
                                {isMobileMenuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
                            </Button>
                        </div>
                        {isMobileMenuOpen && (
                            <div className="md:hidden py-4 glass-card mt-2 animate-fade-in-up">
                                <div className="flex flex-col space-y-4">
                                    {navItems.map((item) => (
                                        <button key={item.name} onClick={() => scrollToSection(item.href)} className="text-left px-4 py-2 text-muted-foreground hover:text-primary hover:bg-primary/10 rounded-lg transition-all duration-300">{item.name}</button>
                                    ))}
                                </div>
                            </div>
                        )}
                    </div>
                    <div className={`absolute bottom-0 left-0 w-full h-px bg-gradient-flow transition-opacity duration-300 ${isScrolled ? 'opacity-50' : 'opacity-0'}`}></div>
                </nav>
            );
        };

        // --- ProjectsSection Component ---
        const ProjectsSection = () => {
            const projects = [
                { title: "Real-Time AQI Analysis & Travel Guidance System", description: "Advanced system using Python, Flask, OpenWeatherMap API, and Leaflet.js for real-time air quality monitoring and intelligent travel recommendations.", technologies: ["Python", "Flask", "API", "Leaflet.js"], icon: Globe, category: "Full-Stack", gradient: "from-purple-500 to-blue-500", github: "https://github.com/Supreeth44/Real-Time-AQI-Analysis-Travel-Guidance-System" },
                { title: "AI-Powered Educational Assistant", description: "Intelligent educational platform built with Python, Streamlit, LangChain, and OpenAI API for personalized learning experiences.", technologies: ["Python", "Streamlit", "LangChain", "OpenAI"], icon: Brain, category: "AI/ML", gradient: "from-violet-500 to-purple-500", github: "https://github.com/Supreeth44/AI-Powered-Educational-Assistant" },
                { title: "Multilingual Real-Time Communication System", description: "Cutting-edge communication platform using Node.js, Socket.IO, Deepl API, and React for seamless multilingual interactions.", technologies: ["Node.js", "Socket.IO", "API", "React"], icon: MessageSquare, category: "Real-Time", gradient: "from-indigo-500 to-violet-500" }
            ];

            const ProjectCard = ({ project, index }) => {
                const IconComponent = project.icon;
                return (
                    <div className="glass-card p-6 group hover:tech-glow transition-all duration-500 animate-fade-in-up relative overflow-hidden" style={{ animationDelay: `${index * 0.2}s` }}>
                        <div className="flex items-start justify-between mb-6">
                            <div className="flex items-center">
                                <div className={`p-3 rounded-lg bg-gradient-to-r ${project.gradient} mr-4`}><IconComponent className="w-8 h-8 text-white" /></div>
                                <div><span className="px-3 py-1 text-xs font-medium bg-primary/20 text-primary rounded-full">{project.category}</span></div>
                            </div>
                            <Zap className="w-6 h-6 text-accent animate-pulse" />
                        </div>
                        <h3 className="text-xl font-bold text-foreground mb-3 group-hover:text-primary transition-colors">{project.title}</h3>
                        <p className="text-muted-foreground mb-6 leading-relaxed">{project.description}</p>
                        <div className="flex flex-wrap gap-2 mb-6">
                            {project.technologies.map((tech) => <span key={tech} className="px-3 py-1 text-sm bg-secondary/50 text-foreground rounded-full border border-border/50">{tech}</span>)}
                        </div>
                        <div className="flex gap-3">
                            <Button size="sm" className="flex-1 tech-glow hover:accent-glow" onClick={() => project.github && window.open(project.github, '_blank')}><Github className="w-4 h-4 mr-2" />View Code</Button>
                            <Button variant="outline" size="sm" className="border-primary/50 hover:bg-primary/10" onClick={() => alert('Live demo coming soon!')}><ExternalLink className="w-4 h-4 mr-2" />Live Demo</Button>
                        </div>
                        <div className="absolute top-0 left-0 w-full h-1 bg-gradient-flow transform scale-x-0 group-hover:scale-x-100 transition-transform duration-500 origin-left"></div>
                        <div className="absolute bottom-0 right-0 w-1 h-full bg-gradient-flow transform scale-y-0 group-hover:scale-y-100 transition-transform duration-500 origin-bottom"></div>
                    </div>
                );
            };

            return (
                <section id="projects" className="py-20 relative">
                    <div className="container mx-auto px-6 relative z-10">
                        <div className="text-center mb-16">
                            <h2 className="text-4xl font-bold mb-4"><span className="text-glow">Featured Projects</span></h2>
                            <p className="text-xl text-muted-foreground max-w-2xl mx-auto">High-performance applications built with precision and cutting-edge technology.</p>
                            <div className="w-24 h-1 bg-gradient-flow mx-auto mt-6 rounded-full"></div>
                        </div>
                        <div className="grid lg:grid-cols-2 xl:grid-cols-3 gap-8 mb-16">
                            {projects.map((project, index) => <ProjectCard key={project.title} project={project} index={index} />)}
                        </div>
                    </div>
                </section>
            );
        };

        // --- SkillsSection Component ---
        const SkillsSection = () => {
            const skills = {
                technical: [ { name: "Python", level: 90, icon: Code }, { name: "Java", level: 85, icon: Code }, { name: "AI/ML (GenAI, Predictive Modeling)", level: 88, icon: Brain }, { name: "Data Analytics (Tableau, Excel)", level: 85, icon: Database }, { name: "SQL", level: 80, icon: Database }, { name: "Cloud Computing (AWS)", level: 75, icon: Cloud } ],
                soft: [ "Teamwork & Collaboration", "Leadership & Event Management", "Communication", "Problem-Solving", "Adaptability" ]
            };

            const SkillCard = ({ skill, index }) => {
                const IconComponent = skill.icon;
                return (
                    <div className="glass-card p-6 group hover:tech-glow transition-all duration-300 animate-fade-in-up" style={{ animationDelay: `${index * 0.1}s` }}>
                        <div className="flex items-center mb-4">
                            <div className="p-2 rounded-lg bg-primary/10 mr-3 group-hover:bg-primary/20 transition-colors"><IconComponent className="w-6 h-6 text-primary" /></div>
                            <h3 className="font-semibold text-foreground">{skill.name}</h3>
                        </div>
                        <div className="space-y-2">
                            <div className="flex justify-between text-sm"><span className="text-muted-foreground">Proficiency</span><span className="text-primary font-medium">{skill.level}%</span></div>
                            <div className="w-full bg-secondary rounded-full h-2"><div className="h-2 rounded-full gradient-flow" style={{ width: `${skill.level}%`, transition: 'width 1s ease-out', transitionDelay: `${index * 0.1}s` }}></div></div>
                        </div>
                    </div>
                );
            };

            return (
                <section id="skills" className="py-20 relative">
                    <div className="container mx-auto px-6">
                        <div className="text-center mb-16">
                            <h2 className="text-4xl font-bold mb-4"><span className="text-glow">Technical Arsenal</span></h2>
                            <p className="text-xl text-muted-foreground max-w-2xl mx-auto">Optimized technology stack designed for high-performance development and innovation.</p>
                            <div className="w-24 h-1 bg-gradient-flow mx-auto mt-6 rounded-full"></div>
                        </div>
                        <div className="mb-16">
                            <h3 className="text-2xl font-bold text-center mb-8 text-primary">Core Skills</h3>
                            <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                                {skills.technical.map((skill, index) => <SkillCard key={skill.name} skill={skill} index={index} />)}
                            </div>
                        </div>
                        <div>
                            <h3 className="text-2xl font-bold text-center mb-8 text-accent">Soft Skills</h3>
                            <div className="flex flex-wrap justify-center gap-4">
                                {skills.soft.map((skill, index) => (
                                    <div key={skill} className="glass-card px-4 py-2 text-center hover:accent-glow transition-all duration-300 animate-fade-in-up flex items-center gap-2" style={{ animationDelay: `${index * 0.1}s` }}>
                                        <Shield className="w-5 h-5 text-accent" />
                                        <span className="text-foreground font-medium">{skill}</span>
                                    </div>
                                ))}
                            </div>
                        </div>
                    </div>
                </section>
            );
        };

        // --- Main App Component ---
        const App = () => {
            const [toasts, setToasts] = useState([]);

            const addToast = (message) => {
                const id = Date.now();
                setToasts(prev => [...prev, { id, message }]);
            };

            const dismissToast = (id) => {
                setToasts(prev => prev.filter(toast => toast.id !== id));
            };

            return (
                <div className="min-h-screen">
                    <ToastContainer toasts={toasts} dismissToast={dismissToast} />
                    <Navigation />
                    <ScrollTrack />
                    <main>
                        <section id="home"><HeroSection /></section>
                        <SkillsSection />
                        <ExperienceSection />
                        <ProjectsSection />
                        <EducationSection />
                        <ContactSection addToast={addToast} />
                    </main>
                    <FooterSection />
                </div>
            );
        };

        const container = document.getElementById('root');
        const root = ReactDOM.createRoot(container);
        root.render(<App />);
    </script>
    {% endraw %}
</body>
</html>
